
<!doctype html>
<html lang="en">

<head>
  <meta charset="utf-8">
  <title>watermark.js - watermarks in the browser</title>
  <script src="scripts/polyfill.js"></script>
  <script src="scripts/watermark.js"></script>
  <script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/8.5/highlight.min.js"></script>
  <link href='http://fonts.googleapis.com/css?family=Josefin+Slab|Maven+Pro' rel='stylesheet' type='text/css'>
  <link rel="stylesheet" href="css/bootstrap.min.css" />
  <link rel="stylesheet" href="css/bootstrap-theme.min.css" />
  <link rel="stylesheet" href="css/style.css" />
  <link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/8.5/styles/default.min.css">
</head>

<body>
  
  <div class="container">

    <h1 class="text-center"><a href="/watermarkjs/">watermark.js</a></h1>
    <nav>
      <ul>
        <li><a href="images.html">images</a></li>
        <li class="separator">-</li>
        <li><a href="text.html">text</a></li>
        <li class="separator">-</li>
        <li><a href="uploading.html">uploading</a></li>
        <li class="separator">-</li>
        <li><a href="pooling.html">pooling</a></li>
        <li class="separator">-</li>
        <li><a href="docs.html">documentation</a></li>
      </ul>
    </nav>

    <div class="col-xs-12">

      <div class="example" id="composite-image">
        <h2>Composite Images</h2>
        <pre>
          <code class="javascript">
watermark(['/img/shepherd.jpg', '/img/via.png'])
  .image(watermark.image.lowerRight())
  .then(function (img) {
    document.getElementById('composite-image').appendChild(img);
  });
          </code>
        </pre>
      </div>

      <div class="example" id="alpha-image">
        <h2>Alpha Transparency</h2>
        <pre>
          <code class="javascript">
watermark(['/img/forest.jpg', '/img/logo.png'])
  .image(watermark.image.lowerRight(0.5))
  .then(function (img) {
    document.getElementById('alpha-image').appendChild(img);
  });
          </code>
        </pre>
      </div>

      <div class="example" id="text">
        <h2>Text</h2>
        <pre>
          <code class="javascript">
watermark(['/img/field.jpg'])
  .image(watermark.text.lowerRight('MyPhoto', '28px serif', '#fff', 0.5))
  .then(function (img) {
    document.getElementById('text').appendChild(img);
  });
          </code>
        </pre>
      </div>

    </div>
  </div>

  <script>
    // simple composite image
    watermark(['img/shepherd.jpg', 'img/logo.png'])
      .image(watermark.image.lowerRight())
      .then(function (img) {
        var pre = document.querySelector('#composite-image pre');
        pre.parentNode.insertBefore(img, pre);
      });

    // a composite image with transparent watermark
    watermark(['img/forest.jpg', 'img/logo.png'])
      .image(watermark.image.lowerRight(0.5))
      .then(function (img) {
        var pre = document.querySelector('#alpha-image pre');
        pre.parentNode.insertBefore(img, pre);
      });

    // simple text watermark
    watermark(['img/field.jpg'])
      .image(watermark.text.lowerRight('MyPhoto', '28px serif', '#fff', 0.5))
      .then(function (img) {
        var pre = document.querySelector('#text pre');
        pre.parentNode.insertBefore(img, pre);
      });
  </script>

  <script>hljs.initHighlightingOnLoad();</script>
</body>

</html>
