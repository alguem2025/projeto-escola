<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Meu Site de Vídeos e Fotos</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h1>Meu Site de Vídeos e Fotos</h1>
  </header>
  <main>
    <section id="videoSection">
      <h2>Vídeos</h2>
      <div id="videoGallery"></div>
      <input type="file" accept="video/*" id="videoInput" multiple>
    </section>
    <section id="photoSection">
      <h2>Fotos</h2>
      <div id="photoGallery"></div>
      <input type="file" accept="image/*" id="photoInput" multiple>
    </section>
  </main>
  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

header {
  background-color: #333;
  color: #fff;
  padding: 20px;
}

h1 {
  margin: 0;
}

main {
  padding: 20px;
}

section {
  margin-bottom: 30px;
}

h2 {
  margin-top: 0;
}

#videoGallery,
#photoGallery {
  display: flex;
  flex-wrap: wrap;
}

.thumbnail {
  margin: 5px;
}

.thumbnail img {
  max-width: 200px;
  max-height: 200px;
  border: 1px solid #ccc;
}
document.addEventListener('DOMContentLoaded', function () {
  const videoInput = document.getElementById('videoInput');
  const photoInput = document.getElementById('photoInput');
  const videoGallery = document.getElementById('videoGallery');
  const photoGallery = document.getElementById('photoGallery');

  videoInput.addEventListener('change', function (event) {
    const files = event.target.files;
    Array.from(files).forEach(file => {
      const video = document.createElement('video');
      video.controls = true;
      video.src = URL.createObjectURL(file);
      video.classList.add('thumbnail');
      videoGallery.appendChild(video);
    });
  });

  photoInput.addEventListener('change', function (event) {
    const files = event.target.files;
    Array.from(files).forEach(file => {
      const img = document.createElement('img');
      img.src = URL.createObjectURL(file);
      img.classList.add('thumbnail');
      photoGallery.appendChild(img);
    });
  });
});
