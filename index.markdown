---
layout: home
breadcrumbs: /
---

<div id="filter-ui" class="mb-5">
  <div id="example-select"></div>
</div>

<div class="flex flex-wrap -m-3"> 


{% include card.html tags="data repository restful" 
target="base-repo/index.html" 
background="assets/images/disks.jpg"
title="base-repo"
subtitle="A place to be for your data"
content="The base-repo is a generic, general purpose research data repository service. It is offering clear, machine-actionable RESTful interfaces for storing, retrieving and managing research data."
%}

{% include card.html tags="metadata repository restful"
target="metastore/index.html"
background="assets/images/metadata.jpg"
title="MetaStore"
subtitle="Storing consistent metadata"
content="MetaStore is a research data repository service storing metadata documents and schemas. By associating each document with a schema and validating it, quality and consistency are maintained. Supports JSON and XML."
%}

{% include card.html tags="restful"
target="collection-registry/index.html"
background="assets/images/collections.jpg"
title="Collection Registry"
subtitle="Collect, Organize, Share"
content="The Collection Registry allows building collections of digital objects, independent of any repository in order to facilitate data
interoperability, reuse and make collections actionable to be able to cope with ever-increasing amounts and volumes of data."
%}

{% include card.html tags="restful"
target="wap-server/index.html"
background="assets/images/annotation.jpg"
title="Web Annotation Protocol server"
subtitle="The digital sticky note solution"
content="The Web Application Protocol server allows creating and managing annotations following the Web Annotation Data Model (WADM) specified by the World Wide Web Consortium (w3c).
It offers a full implementation of the Web Annotation Protocol (WAP) and can therefore be used standalone to annotate arbitrary digital content."
%}

{% include card.html tags="ui"
target="metadata-editor/index.html"
background="assets/images/editor.png"
title="Metadata Editor"
subtitle="It's about filling in and out"
content="The Metadata Editor is a JavaScript library allowing to generate web forms and validate metadata in an intuitive and generic way."
%}

{% include card.html tags="ui"
target="msc/index.html"
background="assets/images/msc.png"
title="Metadata Standards Catalog"
subtitle="Looking for a standard?"
content="The Metadata Standards Catalog is an information platform for finding and sharing metadata standards and tools. It is based on the outcome of the RDA Metadata Standards Catalog Working Group.
"
%}

{% include card.html tags="data metadata"
target="fairdo-cookbook/index.html"
background="assets/images/cookbook.png"
title="FAIR DO Cookbook"
subtitle="A dish for every occasion"
content="The FAIR DO Cookbook is intended to provide first guidance while entering the world of FAIR Digital Objects. It offers a collection of recipes 
on how to appoach different concepts related to FAIR Digital Objects, i.e., Data Types, and PID Kernel Information Profiles.
"
%}

{% include card.html tags="metadata repository"
target="metadatahub/index.html"
background="assets/images/turntable.png"
title="MetadataHub"
subtitle="One to serve all"
content="The MetadataHub is a framework which acts as a proxy for multiple (metadata) repositories. It implements the 'Turntable API'."
%}

{% include card.html tags="restful fairdo metadata"
target="typed-pid-maker/index.html"
background="assets/images/typed-pid-maker_logo.svg"
title="Typed PID Maker"
subtitle="Makes machine-actionable PIDs"
content="The Typed PID Maker is an entry point to integrate digital resources into the FAIR DO ecosystem. It allows creating, modifying and validating PIDs with typed information or retrieving typed information by their PID. It offers sandboxed PIDs for testing, as well as real Handle PIDs."
%}

{% include card.html tags="restful fairdo metadata"
target="fair-do-lab/index.html"
background="assets/images/fair-do-lab/testbed_preview.png"
title="FAIR DO Lab"
subtitle="An environment blueprint for FAIR DO infrastructures"
content="The FAIR DO Lab is a configurable structure of services to fulfill generic FAIR Digital Object (FAIR DO) use cases. It is a proposal for research which can be configured and extended to specific needs."
%}

{% include card.html tags="data metadata"
target="fairdoscope/index.html"
background="assets/images/fairdoscope/logo.png"
title="FAIR-DOscope"
subtitle="Explore the facets of FAIR Digital Objects"
content="FAIR-DOscope is an easy-to-use, generic FAIR Digital Object viewer and browser. It accepts PIDs of FAIR DOs and presents the associated PID record in a graphical and user-friendly way."
%}

{% include card.html tags="data metadata"
target="ro-crate-java/index.html"
background="assets/images/ro-crate-java_logo.svg"
title="ro-crate-java"
subtitle="A software library to package and link research data"
content="ro-crate-java enables the safe creation and modification of research packages following the RO-Crate specification. These packages allow the machine-readable and human-readable description and documentation of research, making it FAIR."
%}

{% include card.html tags="data engineering repository"
target="dce/index.html"
background="assets/images/dce/dce.png"
title="Data Collections Explorer"
subtitle="Discover engineering datasets"
content="The Data Collections Explorer is an information system for the engineering community to facilitate research of domain specific repositories and databases, as well as datasets published individually by research groups."
%}
</div>


<script>

var myOptions = [
  { label: 'Repository', value: 'repository' },
  { label: 'Data', value: 'data' },
  { label: 'Engineering', value: 'engineering' },
  { label: 'Metadata', value: 'metadata' },
  { label: 'RESTful', value: 'restful' },
  { label: 'UI', value: 'ui' },
  { label: 'FAIR Digital Object', value: 'fairdo' }
];

VirtualSelect.init({
  ele: '#example-select',
  options: myOptions,
  multiple: true
});

var selectionOptions = ['repository', 'data', 'engineering', 'metadata', 'restful', 'ui', 'fairdo'];

document.querySelector('#example-select').setValue(selectionOptions);
filterSelection(selectionOptions);

function filterSelection(values) {
  var x, i, j;
x = document.getElementsByClassName("filterDiv");
for (i = 0; i < x.length; i++) {
    w3RemoveClass(x[i], "show");
}

for (i = 0; i < x.length; i++) {
    for(j=0;j<values.length;j++){
        if (x[i].className.indexOf(values[j]) > -1) w3AddClass(x[i], "show");
    }
};
}

function w3AddClass(element, name) {
  var i, arr1, arr2;
  arr1 = element.className.split(" ");
  arr2 = name.split(" ");
  for (i = 0; i < arr2.length; i++) {
    if (arr1.indexOf(arr2[i]) == -1) {element.className += " " + arr2[i];}
  }
}

function w3RemoveClass(element, name) {
  var i, arr1, arr2;
  arr1 = element.className.split(" ");
  arr2 = name.split(" ");
  for (i = 0; i < arr2.length; i++) {
    while (arr1.indexOf(arr2[i]) > -1) {
      arr1.splice(arr1.indexOf(arr2[i]), 1);     
    }
  }
  element.className = arr1.join(" ");
}

var ui = document.getElementById("filter-ui");
var list = ui.getElementsByClassName("vscomp-dropbox");

list[0].addEventListener("click", function(evt){ 
    filterSelection($('#example-select').val());
});

</script>

