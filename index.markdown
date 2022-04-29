---
layout: home breadcrumbs: /
---

<div id="myBtnContainer">
  <button class="btn rounded-lg shadow-lg active" onclick="filterSelection('all')"> Show all</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('repository')"> Repository</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('data')"> Data</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('metadata')"> Metadata</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('RESTful')"> RESTful</button>
  <button class="btn rounded-lg shadow-lg" onclick="filterSelection('ui')"> UI</button>
</div>

<div class="flex flex-wrap -m-3"> 



  <div class="filterDiv w-full sm:w-1/2 md:w-1/3 flex-col p-3 data repository RESTful">
    <div class="bg-white rounded-lg shadow-lg overflow-hidden flex-1 flex flex-col h-full">
      <div class="bg-cover h-48" style="background-image: url(assets/images/disks.jpg);"></div>
      <div class="h-full p-4 flex-1 flex flex-col" style="">
        <h3 class="mb-4 text-2xl">base-repo</h3>
		<b class="mb-4 text-1xl">a place to be for your data</b>
        <div class="mb-4 text-grey-darker text-sm flex-1">
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. </p>
        </div>
        <a href="base-repo/index.html" class="border-t border-grey-light pt-2 text-xs text-grey hover:text-red uppercase no-underline tracking-wide" style="">more...</a>
      </div>
    </div>  
  </div>

  <div class="filterDiv w-full sm:w-1/2 md:w-1/3 flex-col p-3 metadata repository RESTful">
    <div class="bg-white rounded-lg shadow-lg overflow-hidden flex-1 flex flex-col h-full">
      <div class="bg-cover h-48" style="background-image: url(assets/images/metadata.jpg);"></div>
      <div class="h-full p-4 flex-1 flex flex-col" style="">
        <h3 class="mb-4 text-2xl">MetaStore</h3>
		<b class="mb-4 text-1xl">more fun with metadata</b>
        <div class="mb-4 text-grey-darker text-sm flex-1">
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea, quaerat placeat numquam aspernatur, accusamus magnam neque.</p>
        </div>
        <a href="metastore.html" class="border-t border-grey-light pt-2 text-xs text-grey hover:text-red uppercase no-underline tracking-wide" style="">more...</a>
      </div>
    </div>  
  </div>

   <div class="filterDiv w-full sm:w-1/2 md:w-1/3 flex-col p-3 RESTful">
    <div class="bg-white rounded-lg shadow-lg overflow-hidden flex-1 flex flex-col h-full">
      <div class="bg-cover h-48" style="background-image: url(assets/images/collections.jpg);"></div>
      <div class="h-full p-4 flex-1 flex flex-col" style="">
        <h3 class="mb-4 text-2xl">Collection Registry</h3>
		<b class="mb-4 text-1xl">the data squirrel</b>
        <div class="mb-4 text-grey-darker text-sm flex-1">
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea, quaerat placeat numquam aspernatur, accusamus magnam neque.</p>
        </div>
        <a href="collection-registry.html" class="border-t border-grey-light pt-2 text-xs text-grey hover:text-red uppercase no-underline tracking-wide" style="">more...</a>
      </div>
    </div>  
  </div>

   <div class="filterDiv w-full sm:w-1/2 md:w-1/3 flex-col p-3 ui">
    <div class="bg-white rounded-lg shadow-lg overflow-hidden flex-1 flex flex-col h-full">
      <div class="bg-cover h-48" style="background-image: url(assets/images/editor.png);"></div>
      <div class="h-full p-4 flex-1 flex flex-col" style="">
        <h3 class="mb-4 text-2xl">Metadata Editor</h3>
		<b class="mb-4 text-1xl">it's about filling in and out</b>
        <div class="mb-4 text-grey-darker text-sm flex-1">
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quasi, tempore sapiente eveniet quibusdam ab ea, quaerat placeat numquam aspernatur, accusamus magnam neque.</p>
        </div>
        <a href="metadata-editor.html" class="border-t border-grey-light pt-2 text-xs text-grey hover:text-red uppercase no-underline tracking-wide" style="">more...</a>
      </div>
    </div>  
  </div>
</div>




<script>
filterSelection("all")
function filterSelection(c) {
  var x, i;
  x = document.getElementsByClassName("filterDiv");
  if (c == "all") c = "";
  for (i = 0; i < x.length; i++) {
    w3RemoveClass(x[i], "show");
    if (x[i].className.indexOf(c) > -1) w3AddClass(x[i], "show");
  }
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

// Add active class to the current button (highlight it)
var btnContainer = document.getElementById("myBtnContainer");
var btns = btnContainer.getElementsByClassName("btn");
for (var i = 0; i < btns.length; i++) {
  btns[i].addEventListener("click", function(){
    var current = document.getElementsByClassName("active");
    current[0].className = current[0].className.replace(" active", "");
    this.className += " active";
  });
}
</script>

