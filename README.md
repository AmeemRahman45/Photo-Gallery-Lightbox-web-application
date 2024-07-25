<h1>🎨 Photo Gallery with Lightbox 🎨</h1>
<p>
    Welcome to the Photo Gallery with Lightbox project! This web application showcases a grid of images with an interactive lightbox effect, allowing users to view photos in a larger, more detailed format.
</p>
<br>
<h3>🚀 Features</h3>
<ul>
    <li>🖼 <strong>Image Grid</strong>: Displays a beautiful grid of images for easy browsing.</li>
    <li>🔍 <strong>Lightbox Effect</strong>: Click on any image to open it in a larger, detailed view with a darkened background.</li>
    <li>🔄 <strong>Navigation Controls</strong>: Easily navigate through images with next and previous buttons within the lightbox.</li>
    <li>🔧 <strong>Responsive Design</strong>: The gallery is fully responsive, ensuring a great experience on both desktop and mobile devices.</li>
</ul>
<br>
<h3>🔧 Technologies Used</h3>
<ul>
    <li>HTML: Structure and layout of the gallery.</li>
    <li>CSS: Styling for the image grid and lightbox, including animations and transitions.</li>
    <li>JavaScript: Functionality for the lightbox effect and navigation controls.</li>
</ul>
<br><br>
<h3>📋 Code Explanation</h3>
<ol>
    <li>
        <h4>HTML Structure</h4>
        <pre>
&lt;!DOCTYPE html&gt;: Defines the document type and version of HTML.
&lt;html lang="en"&gt;: Begins the HTML document and specifies English as the language.
&lt;head&gt;: Contains meta-information about the document, such as character encoding, viewport settings, and links to external resources.
    &lt;meta charset="UTF-8"&gt;: Sets the character encoding to UTF-8.
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;: Ensures the page is responsive on all devices.
    &lt;title&gt;: Sets the title of the page that appears in the browser tab.
    &lt;link rel="stylesheet" href="styles.css"&gt;: Links to the external CSS file for styling.
&lt;/head&gt;
&lt;body&gt;: Contains the content of the webpage.
    &lt;div class="gallery"&gt;: A container for the image gallery.
        &lt;img src="image1.jpg" alt="Description of image 1" class="gallery-item"&gt;: Represents an image in the gallery.
        &lt;!-- Repeat the img tag for each image --&gt;
    &lt;/div&gt;
    &lt;div class="lightbox" id="lightbox"&gt;: A container for the lightbox effect.
        &lt;span class="close">&times;&lt;/span&gt;: A button to close the lightbox.
        &lt;img class="lightbox-content" id="lightbox-content"&gt;: Displays the selected image in the lightbox.
        &lt;div class="lightbox-caption" id="lightbox-caption"&gt;: Caption for the lightbox image.
        &lt;a class="prev" onclick="plusSlides(-1)">&#10094;&lt;/a&gt;: Button to view the previous image.
        &lt;a class="next" onclick="plusSlides(1)">&#10095;&lt;/a&gt;: Button to view the next image.
    &lt;/div&gt;
    &lt;script src="scripts.js"&gt;&lt;/script&gt;: Links to the external JavaScript file for functionality.
&lt;/body&gt;
        </pre>
    </li>
    <li>
        <h4>CSS Styling</h4>
        <pre>
body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}

.gallery {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    max-width: 800px;
    margin: 20px auto;
}

.gallery-item {
    width: 100%;
    max-width: calc(33.333% - 10px);
    cursor: pointer;
    transition: transform 0.3s ease;
}

.gallery-item:hover {
    transform: scale(1.05);
}

.lightbox {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.8);
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.lightbox-content {
    max-width: 90%;
    max-height: 80%;
}

.lightbox-caption {
    color: #fff;
    text-align: center;
    margin-top: 10px;
}

.close, .prev, .next {
    cursor: pointer;
    position: absolute;
    top: 50%;
    padding: 16px;
    margin-top: -22px;
    color: white;
    font-weight: bold;
    font-size: 20px;
    transition: 0.3s;
}

.close {
    top: 10px;
    right: 25px;
    font-size: 40px;
}

.prev, .next {
    top: 50%;
    width: auto;
    padding: 16px;
    color: white;
    font-weight: bold;
    font-size: 20px;
    transition: 0.3s;
}

.prev {
    left: 0;
}

.next {
    right: 0;
}

.close:hover, .prev:hover, .next:hover {
    background-color: rgba(0,0,0,0.8);
}
        </pre>
    </li>
    <li>
        <h4>JavaScript Functionality</h4>
        <pre>
document.addEventListener("DOMContentLoaded", function() {
    const galleryItems = document.querySelectorAll(".gallery-item");
    const lightbox = document.getElementById("lightbox");
    const lightboxContent = document.getElementById("lightbox-content");
    const lightboxCaption = document.getElementById("lightbox-caption");
    const closeBtn = document.querySelector(".close");
    let currentIndex = 0;

    galleryItems.forEach((item, index) => {
        item.addEventListener("click", () => {
            lightbox.style.display = "flex";
            lightboxContent.src = item.src;
            lightboxCaption.textContent = item.alt;
            currentIndex = index;
        });
    });

    closeBtn.addEventListener("click", () => {
        lightbox.style.display = "none";
    });

    document.querySelector(".prev").addEventListener("click", () => {
        currentIndex = (currentIndex > 0) ? currentIndex - 1 : galleryItems.length - 1;
        lightboxContent.src = galleryItems[currentIndex].src;
        lightboxCaption.textContent = galleryItems[currentIndex].alt;
    });

    document.querySelector(".next").addEventListener("click", () => {
        currentIndex = (currentIndex < galleryItems.length - 1) ? currentIndex + 1 : 0;
        lightboxContent.src = galleryItems[currentIndex].src;
        lightboxCaption.textContent = galleryItems[currentIndex].alt;
    });
});
        </pre>
    </li>
</ol>
<hr>
