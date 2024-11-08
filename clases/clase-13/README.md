# clase
* * *
## APUNTES ##
* Plantear nuevo proyecto para el final del curso - que no sea demasiado sencillo, pero que tampoco sea un comedero de cabeza
* Software Nix - para instalar paquetes de bibliotecas confiables, haciendo que sea un proceso agilizado
* Le profe dió un momento para que cada estudiante hablase de los procesos individuales (Lo que más les gustó, y lo que más les ha costado a lo largo del curso)
* Le profe habla de sus referentes a lo largo de sus estudios (ejempli: en el MIT) 
* Ley de las 4 P's= Passion, Play...
* Proyecto de Distribución y Aporte a ml5 (documentación, grupo de discord, ilustraciones...)
* Versiones de ml5, actualizar las versiones de los trabajos de Andreas en versión 2024
* Teachable Machine - actualizar los códigos y las versiones versión 2024
* La gestión de hacer un cambio en el modelo de Teachable Machine 

* * * 
## CONCEPTOS ##
* SEYMOUR PAPERT - persona muy relevante, influenció a le profe en muchas de sus aspiraciones
* SOFTWARE - LOGO = una tortuguita, es irónico incluso 
* MITCHEL RESNICK
* scratch.mit.edu 
* Lifelong Kindergarten
* media.mit.edu
* MaKey MaKey
* Crickets

* * *
## PROYECTO TEACHABLE MACHINE ## 
- Componemos los grupos con Constantine Lobos <https://github.com/cottito>, Leandro Méndez <https://github.com/BatmanTheDay27> y Diego Castillo <https://github.com/Dielox-X9>. Este grupo trabajará modificando el código exportado de Teachable Machine, para adapatarlo a una versión compatible para 2024 teniendo un tutorial en español, ya que el código actual está desactualizado y no deja exportar los archivos de manera sencilla a p5, esta moificación agilizará el proceso y simplificará los pasos a seguir de los usuarios.
- https://teachablemachine.withgoogle.com/
- https://github.com/googlecreativelab/teachablemachine-community
- https://github.com/googlecreativelab/teachablemachine-community/blob/master/snippets/markdown/image/tensorflowjs/p5js.md (Link de Código a modificar)

``` javascript
<div>Teachable Machine Image Model - p5.js and ml5.js</div>
<script src="https://cdn.jsdelivr.net/npm/p5@latest/lib/p5.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/p5@latest/lib/addons/p5.dom.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/ml5@latest/dist/ml5.min.js"></script>
<script type="text/javascript">
  // Classifier Variable
  let classifier;
  // Model URL
  let imageModelURL = '{{URL}}';
  
  // Video
  let video;
  let flippedVideo;
  // To store the classification
  let label = "";
  // Load the model first
  function preload() {
    classifier = ml5.imageClassifier(imageModelURL + 'model.json');
  }
  function setup() {
    createCanvas(320, 260);
    // Create the video
    video = createCapture(VIDEO);
    video.size(320, 240);
    video.hide();
    flippedVideo = ml5.flipImage(video);
    // Start classifying
    classifyVideo();
  }
  function draw() {
    background(0);
    // Draw the video
    image(flippedVideo, 0, 0);
    // Draw the label
    fill(255);
    textSize(16);
    textAlign(CENTER);
    text(label, width / 2, height - 4);
  }
  // Get a prediction for the current video frame
  function classifyVideo() {
    flippedVideo = ml5.flipImage(video)
    classifier.classify(flippedVideo, gotResult);
    flippedVideo.remove();
  }
  // When we get a result
  function gotResult(error, results) {
    // If there is an error
    if (error) {
      console.error(error);
      return;
    }
    // The results are in an array ordered by confidence.
    // console.log(results[0]);
    label = results[0].label;
    // Classifiy again!
    classifyVideo();
  }
</script>

```
- Como se ve en el código de GitHub las primeras 5 líneas son las utilizadas en P5:

``` javascript
<div>Teachable Machine Image Model - p5.js and ml5.js</div>
<script src="https://cdn.jsdelivr.net/npm/p5@latest/lib/p5.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/p5@latest/lib/addons/p5.dom.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/ml5@latest/dist/ml5.min.js"></script>
<script type="text/javascript">

```
- Nosotros debemos modificar la línea número 4 que dice:

``` javascript
<script src="https://cdn.jsdelivr.net/npm/ml5@latest/dist/ml5.min.js"></script>
```
- La cambiamos por:

``` javascript
<script src="https://cdn.jsdelivr.net/npm/ml5@0.12.2/dist/ml5.min.js"></script>
```

- Este cambio en el código permite la lectura y funcionamiento correcto.

