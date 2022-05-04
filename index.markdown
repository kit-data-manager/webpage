---
layout: home 
breadcrumbs: /
---

<div>
    <div class="container">
        <div class="carousel">
            <input type="radio" name="slides" checked="checked" id="slide-1">
            <input type="radio" name="slides" id="slide-2">
            <input type="radio" name="slides" id="slide-3">
            <input type="radio" name="slides" id="slide-4">
            <input type="radio" name="slides" id="slide-5">
            <input type="radio" name="slides" id="slide-6">
            <ul class="carousel__slides">
                <li class="carousel__slide">
                    <figure>
                        <div>
                            <img src="https://picsum.photos/id/1041/800/450" alt="">
                        </div>
                        <figcaption>
                            Lorem ipsum dolor sit amet consectetur adipisicing elit.
                            <span class="credit">Photo: Tim Marshall</span>
                        </figcaption>
                    </figure>
                </li>
                <li class="carousel__slide">
                    <figure>
                        <div>
                            <img src="https://picsum.photos/id/1043/800/450" alt="">
                        </div>
                        <figcaption>
                            Lorem ipsum dolor sit amet consectetur adipisicing elit.
                            <span class="credit">Photo: Christian Joudrey</span>                            
                        </figcaption>
                    </figure>
                </li>
                <li class="carousel__slide">
                    <figure>
                        <div>
                            <img src="https://picsum.photos/id/1044/800/450" alt="">
                        </div>
                        <figcaption>
                            Lorem ipsum dolor sit amet consectetur adipisicing elit.
                            <span class="credit">Photo: Steve Carter</span>                            
                        </figcaption>
                    </figure>
                </li>
                <li class="carousel__slide">
                    <figure>
                        <div>
                            <img src="https://picsum.photos/id/1045/800/450" alt="">
                        </div>
                        <figcaption>
                            Lorem ipsum dolor sit amet consectetur adipisicing elit.
                            <span class="credit">Photo: Aleksandra Boguslawska</span>                            
                        </figcaption>
                    </figure>
                </li>
                <li class="carousel__slide">
                    <figure>
                        <div>
                            <img src="https://picsum.photos/id/1049/800/450" alt="">
                        </div>
                        <figcaption>
                            Lorem ipsum dolor sit amet consectetur adipisicing elit.
                            <span class="credit">Photo: Rosan Harmens</span>                            
                        </figcaption>
                    </figure>
                </li>
                <li class="carousel__slide">
                    <figure>
                        <div>
                            <img src="https://picsum.photos/id/1052/800/450" alt="">
                        </div>
                        <figcaption>
                            Lorem ipsum dolor sit amet consectetur adipisicing elit.
                            <span class="credit">Photo: Annie Spratt</span>                            
                        </figcaption>
                    </figure>
                </li>
            </ul>    
            <ul class="carousel__thumbnails">
                <li>
                    <label for="slide-1"><img src="https://picsum.photos/id/1041/150/150" alt=""></label>
                </li>
                <li>
                    <label for="slide-2"><img src="https://picsum.photos/id/1043/150/150" alt=""></label>
                </li>
                <li>
                    <label for="slide-3"><img src="https://picsum.photos/id/1044/150/150" alt=""></label>
                </li>
                <li>
                    <label for="slide-4"><img src="https://picsum.photos/id/1045/150/150" alt=""></label>
                </li>
                <li>
                    <label for="slide-5"><img src="https://picsum.photos/id/1049/150/150" alt=""></label>
                </li>
                <li>
                    <label for="slide-6"><img src="https://picsum.photos/id/1052/150/150" alt=""></label>
                </li>
            </ul>
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

