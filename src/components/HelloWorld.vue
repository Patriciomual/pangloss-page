<template>
  <div>
    <v-card class="overflow-hidden">
      <v-app-bar
        color="#6A76AB"
        dark
        prominent
        style="border-radius: 0px"
        width="100%"
        src="https://firebasestorage.googleapis.com/v0/b/trafla-24d65.appspot.com/o/trafla%2Fplanet.png?alt=media&token=f01b1458-30a3-4fc6-8918-bd286ec96194"
        
      >
        <template v-slot:img="{ props }">
          <v-img
            v-bind="props"
            gradient="to top right, rgba(144,21,21,10), rgba(7,6,169,.5)"
          ></v-img>
        </template>
          
          <h1 class="letra" style="margin:1%">PANGLOSS</h1><br>
          <span style="font-size:14px;margin-top:3.5%">v0.1.2</span>
          
          <br><br>
      </v-app-bar>


    </v-card>   
    <v-container>
      <v-row class="text-center">
        <v-col cols="12">
          <div>
            <p class="letra1" style="text-align:center">
              Dynamic tutorial cards
            </p> <br>
            <p class="letra1" style="text-align:center">
              Pangloss es un componente dinámico para tutoriales construido utilizando Vue en su versión 2 y Vuetify.<br>
              Basado en el componente Steppers de vuetify que permite mostrar el progreso del contenido en pasos enumerados.
            </p><br>
            <h2 class="letra" style="text-align:left">Demo</h2> <br>
            <center>
            <v-btn v-if="!view" @click="view=true" outlined rounded>
              abrir tutorial
            </v-btn> <br>
            </center>
            <pangloss v-if="view" :data.sync="datos" @finish="a=>(view = a)"></pangloss>



            <br>
            <h2 class="letra" style="text-align:left">Install</h2> <br>
            <v-card outlined class="letra-caja" style="background-color: #f4f4ed">
              <pre>npm i pan-gloss</pre>
            </v-card> <br>
            <h2 class="letra" style="text-align:left">Quick Start</h2> <br>
            <p  class="letra1">Lo primero que necesitas despues de instalar el componente en tu proyecto es importarlo en <mark>main.js</mark>. Ésta es la forma
              global, ya que posteriormente no será necesario importar nada en el componente vue que deciemos utilizar, por ende tal como se puede deducir,
            si existe una forma global de instalación existe una manera local. <br><br> Revisemos la fomar global:</p> <br>
            <v-card outlined class="letra-caja" style="background-color: #f4f4ed">
              <pre>
                <code>
                  import 'pan-gloss/pan-gloss.css';
                  import * as pangloss from 'pan-gloss';

                  Vue.use({install: pangloss.install})
                </code>
              </pre>
            </v-card> <br>
            <p class="letra1">
              De ésta manera el componente queda listo para ser usado de la forma <mark> &lt;pangloss&gt;&lt;/pangloss&gt; </mark>
            </p><br>
            <p class="letra1">
              En el template del componente .vue que estamos utilizando:
            </p><br>
            <v-card outlined class="letra-caja" style="background-color: #f4f4ed">
              <pre class="language-javascript">
                <code class="language-javascript">
                  &lt;template&gt;
                    &lt;pangloss v-if="view" :data.sync="datos" @finish="a=>(view = a)"&gt;&lt;/pangloss&gt;
                  &lt;/template&gt;
                </code>
              </pre>
            </v-card> <br>
            <p class="letra1">
              Vemos como el componente está haciendo uso de algunas directivas y recibiendo algunos datos, esto se debe principalmente a la naturaleza del componente,
              ya que probablemente solo deba mostrarse en algunas ocaciones, como la primera vez del usuario en tu aplicación, por ejemplo, por eso es que usamos <i>v-if</i> 
              para mostrar el componente solo cuando <i>view</i> sea <i>True</i>, entonces al mismo tiempo debemos recibir el cambio en <i>view</i> cuando se termina el tutorial y queramos dejar de mostrar
              el componente. Entonces <i>finish</i> emite el booleano <i>False</i> desde el componente pangloss cuando el tutorial haya terminado, lo recibimos con la variable <i>"a"</i> y asignamos
              el valor a <i>view</i> ocultando el módulo oportunamente.
            </p><br>          
            <p class="letra1">
              Por último vemos que se ocupa una directiva <i>v-bind</i> con su abreviación <i>":data.sync"</i> de forma síncrona para capturar en tiempo real cualquier cambio
              que se produzca en el <mark>Object</mark> que se debe enviar con los datos que cargarán al componente.
            </p><br> 

            <p class="letra1">
              La forma de enviar datos al componente pangloss es por medio de un objeto con multiples propiedades que controlarán desde la apariencia hasta el contenido del tutorial. <br>
            </p><br>   


            <v-card outlined class="letra-caja" style="background-color: #f4f4ed">
              <pre>
                  &lt;script&gt;
                    export default {
                      name: 'HelloWorld',
                      data: () => ({
                          view : true,
                          datos: {
                              width:'100%',
                              height: '400px',
                              color: 'linear-gradient(140deg, #aa0606, #0606aa)',
                              steps : ['uno','','tres'],
                              content: [
                                {
                                    text:'Texto contenido del primer paso',
                                    textPosition: 'center',
                                    textSize: '25px',
                                    image:'https://url-de-imagen',
                                    imageSize: '70%',
                                    btnName: 'conoce a pangloss',
                                    btnHref: 'http://trafla.org/',
                                    btnColor: 'cyan',
                                    btnPosition: 'left'
                                },
                                {
                                    text:'segundo',
                                    textPosition: 'left',
                                    textSize: '15px',
                                    image: null,
                                    imageSize: '50%'
                                },
                                {
                                    text:'tercero',
                                    textPosition: 'center',
                                    textSize: '15px',
                                    image: null,
                                    imageSize: '50%'
                                },
                              ],
                          }
                      }),
                    }
                  &lt;/script&gt;
              </pre>
            </v-card> <br>
            <h2 class="letra" style="text-align:left">Data</h2> <br>
            <p class="letra1">
              Cada uno de las propiedades del objeto <i>data</i> tiene un efecto sobre el componente, pasaremos a explicar cada una de ellas: <br><br>
            </p><br>   
            <h3 class="letra" style="text-align:left">Configuración general</h3>
            <p class="letra1">
             
              <ul>
                <li>
                  width : Regula el tamaño de forma horizontal del componente, puede expresar el tamaño en <i>%</i> o <i>px</i>.
                </li>
                <li>
                  height : Regula el tamaño de forma vertical del componente, puede expresar el tamaño en <i>%</i> o <i>px</i>.
                </li>
                <li>
                  color : Regula el color de fondo del componente, lo hace a través de css y su función <i>linear-gradient</i>, por ende se pueden tener un fondo
                  con una combinación de colores en gradiente, el primer parametro que recibe la función son los grados en que se juntan los colores, y los otros dos son
                  parametros de colores. <br> <i>Nota:</i> Si se quiere un solo color de fondo basta con que ambos argumentos reciban el mismo color.
                </li>
                <li>
                  <mark>steps :</mark> Esta es la propiedad más importante ya que define la cantidad de pasos que tendra nuestro tutorial. <br>
                  <i>pangloss</i> itera este <i>array</i> generando tarjetas en el componente <i>Steppers</i> las que contendrán el conenido de cada paso del tutorial. <br><br>
                  <i>Nota:</i> el nombre que pongamos en cada elemento del array será el nombre del paso en el tutorial, podemos dejar el elemento vacio <i>' '</i> para mostrar solo el 
                  número del paso en el componente Steppers.
                </li>
              </ul>
            </p><br>
            <h3 class="letra" style="text-align:left">Contenido</h3><br>
            <p class="letra1">
              Todo el contenido de nuestro tutorial será definido en un <i>Object</i> que encontramos dentro del array <i>Content</i>. <br>
              Este <i>Array de objetos</i> será ciclado dentro de cada una de las tarjetas que se definieron gracias al ciclo de <i>Steps</i>. <br><br>
              <mark>importante</mark> La cantidad de objetos que se defina debe ser igual que la cantidad de pasos, definidas en <i>Steps</i> para evitar errores. <br><br>
            </p>
            <p class="letra1">
              <ul>
                <li>
                  text : Contiene el texto a mostrar.
                </li>
                <li>
                  textPosition : Responde a la función <i>text-align</i> de css que regula la posición del texto, permitiendo <i>left, center, right</i>.
                </li>
                <li>
                  textSize : Regula el tamaño de la letra. 
                </li>
                <li>
                  image : Permite incrustar la <i>url</i> de una imagen en el lado izquierdo de nuestro tutorial. <br>
                  <i>Nota: </i>Si no se desea imagen poner <i>null</i>. <br>
                </li>
                <li>
                  imageSize : Tamaño de la imagen.
                </li> <br>
                <mark>importante</mark> las propiedades descritas a continuación pueden no ser usadas si no son requeridas <i>ver segundo objeto del ejemplo</i>. <br><br>
                <li>
                  btnName : Permite incrustar un boton al final del texto del tutorial.
                </li>
                <li>
                  btnHref : <i>Url</i> a la que redireccionará el botón.
                </li>
                <li>
                  btnColor : Color del botón.
                </li>
                <li>
                  btnPosition : Posición del botón <i>left, center, right</i>.
                </li>
              </ul>
            </p>
          </div>
        </v-col>
      </v-row>
      <v-row>
        <p class="letra1">Revisa el código fuente:</p>
        <v-col cols="12">
          <v-card
            class="mx-auto"
            max-width="100%"
            style="background-color: #e5dcdc"
            outlined
          >
            <v-list-item three-line>
              <v-list-item-content>
                <div class="overline">
                  <v-icon>mdi-book</v-icon>
                  <span class="letra1"><a style="text-decoration:none" href="https://github.com/Patriciomual/pangloss">Patriciomual/pangloss</a></span>
                </div> <v-divider></v-divider>
                <v-list-item-title class="headline mb-1">
                  <samp>
                      Dynamic tutorial cards <br> <span><a href="https://github.com/Patriciomual/pangloss#readme">Read More</a></span>
                  </samp>
                  
                </v-list-item-title>
              </v-list-item-content>

              <v-list-item-avatar
                tile
                size="80"
                color="grey"
              >
              <img  src="https://www.pikpng.com/pngl/b/247-2473934_image-freeuse-download-png-icon-free-download-onlinewebfonts.png" alt="">
              </v-list-item-avatar>
            </v-list-item>
              <span class="letra1" style="font-size:15px;margin:2%">
                <a style="text-decoration:none" href="https://github.com/Patriciomual/pangloss">https://github.com/Patriciomual/pangloss</a></span>
              <v-btn
                text
                outlined
                rounded
                small
                href="https://github.com/Patriciomual/pangloss/zipball/main"
                style="margin:1%"
              >
                Download as zip
              </v-btn>
          </v-card>
        </v-col>

      </v-row> <br>
      <v-divider></v-divider> <br>
      <v-row>
            <h2 class="letra" style="text-align:left">pangloss</h2> <br><br><br>

            <v-card style="color:white" outlined class="color-tarjeta">
              <blockquote class="letra1" style="font-size:15px;text-align:justify;margin:3%;padding:2%">            

                <q>Pangloss es un personaje de Cándido, novela del escritor francés Voltaire. Es el tutor de Cándido durante su estancia en el castillo alemán de Thunder-ten-tronckh, en Westfalia, 
                y posteriormente se une a Cándido en algunas de sus desventuras. Como la mayoría de los personajes de Cándido, Pangloss es un "personaje plano": posee sólo leves rasgos psicológicos 
                que no evolucionan demasiado a lo largo de la historia.

                Pangloss es un seguidor del filósofo Gottfried Leibniz, o como muchos han señalado, su caricatura o sencillamente su sátira, el cual en su Teodicea afirmó que vivimos en «el mejor 
                de los mundos posibles».
                </q>
                <footer>
                  <cite><a style="color:white" href="https://es.wikipedia.org/wiki/Pangloss">seguir leyendo en wikipedia</a></cite>
                </footer>
              </blockquote>
            </v-card> <br>
          <v-card
            max-width="100%"
            flat
            style="color:black;margin:2%"
          >
            <div class="overline">
              <h3 class="letra">Y si me doy la libertad de soñar un poco...</h3>
              <p class="letra1" >Concepto:</p> <br>
              <p class="letra1"> 
                 <img width="50%" style="float: right;margin-top:-15%"  src="https://firebasestorage.googleapis.com/v0/b/trafla-24d65.appspot.com/o/trafla%2Fpangloss_cuerpoCompleto.gif?alt=media&token=7d5326d9-8a66-4b0a-ad5c-c1dab40d1fcb" alt="">
                pangloss como personaje esta pensado como un viajero del espacio y el tiempo en una realidad donde los multiples universos son un hecho innegable. 
                <br> Un universo que ha sido destrozado por el cataclismo <i>lighter-fluid</i>
                que ha dejado a todo ser viviente en un estado gaseoso, con sus moléculas elementales divididas.
                En nuestro universo que será llamado <i>known-branch</i> se ha encontrado, gracias a la presente computación cuantica,
                un número sumamente raro derivado de secuencias repetidas de los decimales de pi.
                Éste número al ser trascrito a hexadecimal a formado la frase <i>"el mejor de los mundos posibles"</i>                   
              </p>
            </div> <br>
            <h2 class="letra" style="text-align:left">Definitivamente este componente continuará...</h2>
          </v-card>
      </v-row>
    </v-container>
    <v-footer style="background: black">
      <a href="https://yavu.org/">
        <img width="20%" src="https://firebasestorage.googleapis.com/v0/b/trafla-24d65.appspot.com/o/trafla%2Flogo_yavu_waxe.png?alt=media&token=e85a1dc2-dd26-49ca-afb5-757cf6306051" alt="yavu-logo">
      </a>
    </v-footer>
  </div>
</template>
<script>
  export default {
    name: 'HelloWorld',
    data: () => ({
      view : true,
      datos: {
          width:'100%',
          height: '400px',
          color: 'linear-gradient(140deg, #aa0606, #0606aa)',
          steps : ['primer paso','segundo paso',''],
          content: [
            {

                text:'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Temporibus cumque saepe, quae, eius architecto accusamus voluptatem dolores velit nisi asperiores perferendis ipsam doloribus. Laborum omnis neque voluptatibus officia ea tempora.',
                textPosition: 'left',
                textSize: '1.1em',
                image:'https://firebasestorage.googleapis.com/v0/b/trafla-24d65.appspot.com/o/trafla%2FNew%20Piskel%20(2).gif?alt=media&token=59884834-5748-4d2b-a3b5-040aee3ff30d',
                imageSize: '50%',
                btnName: 'conoce trafla',
                btnHref: 'http://trafla.org/',
                btnColor: 'cyan',
                btnPosition: 'left'
            },
            {
                text:'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Temporibus cumque saepe, quae, eius architecto accusamus voluptatem dolores velit nisi asperiores perferendis ipsam doloribus. Laborum omnis neque voluptatibus officia ea tempora.',
                textPosition: 'left',
                textSize: '25px',
                image: null,
                imageSize: '50%'
            },
            {
                text:'Lorem ipsum, dolor sit amet consectetur adipisicing elit. Temporibus cumque saepe, quae, eius architecto accusamus voluptatem dolores velit nisi asperiores perferendis ipsam doloribus. Laborum omnis neque voluptatibus officia ea tempora.',
                textPosition: 'center',
                textSize: '25px',
                image: null,
                imageSize: '50%'
            },
          ],
      }
  
    }),
  }
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300&family=Open+Sans:wght@300&display=swap');

mark{
  background-color: #aa0606;
  color: white;
  padding: .1%;
  border-radius: 3px;
}
pre{
  overflow:auto;
  padding:10px;
  margin:12px 0 10px;
  font-size:0,9em;
}
code{
  white-space:pre-wrap;
}
li{
  margin: 1%;
}
.letra-caja{
  padding: 1%;
}
.letra{
  font-family: 'Montserrat', sans-serif;
  text-align: center;
}
.letra1{
  font-family: 'Open Sans', sans-serif;
  text-align: justify;
  font-size: 18px;
}
.color-tarjeta{
  background-image: linear-gradient(160deg, #aa0606, #fcf088);
}
</style>