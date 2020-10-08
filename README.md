<div id="toc_container">
<p class="toc_title">Table of Contents</p>
<ul class="toc_list">
<li><a href="#question_1">Introduction</a>
<li><a href="#question_2">Concept</a>
<li><a href="#question_3">Data</a>
<li><a href="#question_4">Pre-processing</a>
<li><a href="#question_6">The Maps</a>
</ul>
</div>

<br>

<h1 id="question_1">Introduction</h1>

This code-through will show how to take open data addresses and turn them into an interactive map using the **[Leaflet](https://cran.r-project.org/web/packages/leaflet/index.html)** package. I will take addresses from the Phoenix Public Library system and plot these on a map, with markers that provide additional useful information about the libraries. The goal is to have a single page where people can go to find which library would be most useful to their needs. This map could also be embedded on the public library website to inform patrons. 

<br>

<h2 id="question_2">Concept</h2>

This project built on information in a [**Towards Data Science**](https://towardsdatascience.com/making-interactive-maps-in-r-with-less-than-15-lines-of-code-bfd81f587e12) Medium post by Brandon Walker. 

<br>

<h2 id="question_3">Data</h2>

These maps were built using data from the [**Phoenix, AZ Open Data Portal**](https://www.phoenixopendata.com/dataset/libraries/resource/b7158429-b69e-4f87-8a96-b4857c6d65b5). The data was not linked through the API (since it was broken at the time of creation) so the data is static as of 10/1/2020.

<br>

<h2 id="question_4">Pre-processing</h2>

The data from this portal is fairly minimal and requires very little preprosessing. For **[Leaflet](https://cran.r-project.org/web/packages/leaflet/index.html)** to work properly, we need more than just the address of the library - which is provided in the dataframe under `libraries$AddressFull`.

<br>

<h1 id="question_6">The Maps</h1>

