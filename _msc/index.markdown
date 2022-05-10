---
title: Metadata Standards Catalog
breadcrumbs: /msc/
layout: default
description: A catalog for your metadata standards and tools.
navigation_id: msc_index
tag-name: msc
---

# The Metadata Standards Catalog

The Metadata Standards Catalog is an information platform for users looking for metadata standards and metadata tools fitting their needs. 
With more than 100 metadata standards and around 80 tools the catalog offers a perfect start into the field of research data management.
The Metadata Standards Catalog is based on the output of the [RDA Metadata Standards Catalog WG](https://www.rd-alliance.org/groups/metadata-standards-catalog-working-group.html)
and has been slightly adopted in terms of layout and filtering. Furthermore, this instance of the catalog is not in a final state
but can, should, and will be extended by new standards and tools by the community. 

## Features

* Easy-to-use Web interface based on the RDA Metadata Standards Catalog v1
* Filtering for metadata standards by research field on the main page
* More than 100 metadata standards and around 80 metadata tools already registered
* [MetaStore instance](/webpage/metastore/index.html) running in the backend allowing to register machine-readable schemas for metadata standard

## Impressions

{% include gallery.html %}

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
