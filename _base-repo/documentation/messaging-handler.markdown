---
title:  "Adding a Custom Message Handler"
breadcrumbs: /base-repo/documentation/messaging-handler
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

### {{ page.title }}

There are multiple possibilities to consume messages from a server supporting the Advanced Message Queuing Protocol (AMQP) like RabbitMQ. In this documentation, we'll describe how to do this using the built-in messaging support. 
Therefore, it's beneficial if you already have some programming experiences, preferably in Java. 
In the code repository there exists an example handler which is part of this project: [https://github.com/kit-data-manager/generic-message-consumer]()

You may now open your preferred development environment and clone the project from GitHub.

After building the generic-message-consumer project, the sample-handler project can be opened from the same project folder. This project consists of one source file named 'LoggingMessageHandler.java' implementing the 'IMessageHandler' interface. 
This interface offers three methods, whereas two have to be implemented: 

1. getHandlerIdentifier(): This method allows to (optionally) return a custom handler identifier, e.g. a unique name and implementation version. By default, the class name is returned.
2. configure(): This method is called at instantiation time and allows loading and validating handler-specific properties. The handler will be available only if configure() returns 'true'. Otherwise, the handler is deactivated.
3. handle(BasicMessage message): This method is called for each and every message received by the repository's message queue. Thus, a handler should decide first if the message should be handled or not. If not, it might be rejected.

```java
@Component
public class LoggingMessageHandler implements IMessageHandler{

  private static final Logger LOGGER = LoggerFactory.getLogger(LoggingMessageHandler.class);

  @Override
  public RESULT handle(BasicMessage message){
    LOGGER.debug("Successfully received message {}.", message);
	//Typically, we should now return 'RESULT.SUCCEEDED' as we successfully processed the message.
    //However, as we actually did not touch the message we pretend to reject the message. Thus, 
    //the message receiver won't expect the message to be handled successfully if this sample
    //handler is the only working handler installed, while all other handlers are failing.
    return RESULT.REJECTED;
  }

  @Override
  public boolean configure(){
    //no configuration necessary
    return true;
  }

}
```

The code snippet above shows the implementation of the aforementioned interface for the sample-handler. You can see that no configuration is needed for this handler, 'getHandlerIdentifier' is not overwritten, therefore the default identifier
is 'LoggingMessageHandler' and the only thing which is done is logging the message. One remarkable thing of this sample is the return value of the 'handle' method. As described in the code comment, we return REJECTED in order to not mark the 
message as 'handled' in the scheduler. The reason for doing this can be clarified by the following description of the scheduling process:

1. The scheduler polls every second (default, can be changed in application.properties) for the next message in the queue.
2. The message is presented to all successfully configured handlers.
3. The first handler which returns 'SUCCEEDED' activates a flag 'messageHandledByOne'. 
4. If a handler returns 'FAILED', the message and the handler name are preserved in a file called 'failed_message_handles.csv' for later processing. If this succeeds once, the flag 'messageHandledByOne' is also set.
5. If 'REJECTED' is returned by a handler, the scheduler proceeds to the next handler without setting the flag 'messageHandledByOne' nor preserving the message.
6. If the flag 'messageHandledByOne' is not set after all handlers were called, the message is logged to the logfile as debug entry and will be discarded.

Thus, if we in our sample handler wouldn't return 'REJECTED', our status would influence how the scheduler deals with the message based on our response, which is nothing we want for a handler only logging the message.

After implementing a custom message handler you have to build a jar file and place it, together with all required dependencies, in the extensions folder of your KIT DM 2.0 installation. If your handler needs any configuration, 
it is recommended to place it in the current working directory at service startup, which is typically the folder where 'base-repo.jar' is located.
