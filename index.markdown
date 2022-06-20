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
subtitle="a place to be for your data"
content="The base-repo is a generic, general purpose research data repository service offering clear, machine-actionable RESTful interfaces for storing, retrieving and managing research data."
%}

{% include card.html tags="metadata repository restful"
target="metastore/index.html"
background="assets/images/metadata.jpg"
title="MetaStore"
subtitle="more fun with metadata"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea, quaerat placeat numquam aspernatur, accusamus magnam neque."
%}

{% include card.html tags="restful"
target="collection-registry/index.html"
background="assets/images/collections.jpg"
title="Collection Registry"
subtitle="collect, organize, share"
content="The Collection Registry allows building collections of digital objects, independent of any repository in order to facilitate data
interoperability, reuse and make collections actionable to be able to cope with ever-increasing amounts and volumes of data."
%}

{% include card.html tags="ui"
target="metadata-editor/index.html"
background="assets/images/editor.png"
title="Metadata Editor"
subtitle="it's about filling in and out"
content="The Metadata Editor is a JavaScript library allowing to generate web forms and validate metadata in an intuitive and generic way."
%}

{% include card.html tags="ui"
target="msc/index.html"
background="assets/images/msc.png"
title="Metadata Standards Catalog"
subtitle="looking for a standard?"
content="The Metadata Standards Catalog is an information platform for finding and sharing metadata standards and tools. It is based on the outcome of the [Metadata Standards Catalog Working Group](https://www.rd-alliance.org/groups/metadata-standards-catalog-working-group.html).  
"
%}

{% include card.html tags="data metadata"
target="fairdo-cookbook/index.html"
background="assets/images/cookbook.png"
title="FAIR DO Cookbook"
subtitle="a dish for every occasion"
content="Todo.  
"
%}

{% include card.html tags="restful fairdo metadata"
target="typed-pid-maker/index.html"
background="assets/images/typed-pid-maker_logo.svg"
title="Typed PID Maker"
subtitle="makes machine-actionable PIDs."
content="The Typed PID Maker is an entry point to integrate digital resources into the FAIR DO ecosystem. Create, modify, validate and retrieve PIDs for your digital objects. Offers sandboxed PIDs for testing, but can be configured to, e.g, the Handle system."
%}

{% include card.html tags="restful fairdo metadata"
target="fair-do-lab/index.html"
background="assets/images/fair-do-lab/testbed_preview.png"
title="FAIR DO Lab"
subtitle="an environment blueprint for FAIR DO infrastructures."
content="The FAIR DO Lab is a configurable structure of services to fulfill generic FAIR Digital Object (FAIR DO) use cases. It is a proposal for research which can be configured and extended to specific needs."
%}

{% include card.html tags="data metadata"
target="ro-crate-java/index.html"
background="assets/images/ro-crate-java_logo.svg"
title="ro-crate-java"
subtitle="a library to package and link all your research data."
content="Using ro-crate-java, you can create and modify research packages (RO-Crates). These packages allow you to describe your research machine-readable and human-readable, making it FAIR. Build this functionality into your applications or use it directly."
%}
</div>


<script>

var myOptions = [
  { label: 'Repository', value: 'repository' },
  { label: 'Data', value: 'data' },
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

document.querySelector('#example-select').setValue(['repository', 'data', 'metadata', 'restful', 'ui', 'fairdo']);
filterSelection(['repository', 'data', 'metadata', 'restful', 'ui', 'fairdo']);

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

