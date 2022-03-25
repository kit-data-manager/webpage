```http
POST /api/v1/dataresources/edbf964c-f215-4fc6-9ef1-2ff1ea5a811e/data/randomFile2.txt HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Host: localhost:8080

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=file; filename=randomFile2.txt
Content-Type: multipart/form-data

I7a7EvgrdmDPXVL0tWbqCY6iKwy0D7T0Wx4bvev5juu3Kf89VySewuvNLaUFgBB4
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=metadata; filename=metadata.json
Content-Type: application/json

{"versioningService":"none","depth":0,"size":0,"metadata":{"test":"ok"},"tags":[]}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```