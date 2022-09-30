---
title: Data Collections Explorer
breadcrumbs: /dce/
layout: default
description: An information system for the engineering sciences.
navigation_id: dce_index
tag-name: dce
---

# The Data Collections Explorer

Easy findability and accessibility are important for the efficient re-use of research data. The Data Collections Explorer is an information system for engineers looking for discipline specific repositories, archives, databases, and individually published datasets. It aims to help answer the following questions:
- Are there datasets available to support my research questions?
- Are benchmarks available to check my results?
- Are datasets published Open Access?
- Where to publish my research datasets?
- Are there size limitations for datasets?
- Are there publication costs?

## Features

* Filtering for type, subject area, Open Access
* Full-text search of the entries
* Constantly updated based on community feedback

## Impressions

{% include dce-gallery.html %}

<script>
    let slideIndex = 1;
    showSlides(slideIndex);

    // Next/previous controls
    function plusSlides(n) {
        showSlides(slideIndex += n);
    }

    // Thumbnail image controls
    function currentSlide(n) {
        showSlides(slideIndex = n);
    }

    function showSlides(n) {
        let i;
        let slides = document.getElementsByClassName("mySlides");
        let dots = document.getElementsByClassName("demo");
        let captionText = document.getElementById("caption");
        if (n > slides.length) {slideIndex = 1}
        if (n < 1) {slideIndex = slides.length}
        for (i = 0; i < slides.length; i++) {
            slides[i].style.display = "none";
        }
        for (i = 0; i < dots.length; i++) {
            dots[i].className = dots[i].className.replace(" active", "");
        }
        slides[slideIndex-1].style.display = "block";
        dots[slideIndex-1].className += " active";
        captionText.innerHTML = dots[slideIndex-1].alt;
    }

</script>
