# Como subir imagenes a Cloudinary con [MF Dev](https://www.youtube.com/channel/UC4r9fia857HbFKswu9YqaCg, "Canal Oficial MF Dev")
---

## Pasos a seguir 

### 1º Crear proyecto
Para comenzar vamos a crear un proyecto de react con vite, para ello vamos a usar el instalador de paquete de Node js llamado `npm`, primero abrimos una terminal integrada en Visual Studio Code y ejecutamos el siguiente comando:

`npm create vite@latest`

Una vez ejecutado el comando nos va a preguntar como queremos que se llame el proyecto, para este caso solo vamos a llamarlo `client` ya que es el nombre que usualmente se le da a los proyectos de **Frontend**. Luego nos va a preguntar que tipo de proyectos queremos crear, nosotros usaremos el de `react`. Proximo a esto nos preguntara con que lenguaje vamos a querer usar en nuestro proyecto, para este caso usaremos `Javascript + SWC` ya que el compilador que usa es mas rápido que el convencional. Cuando termine de crear el proyecto accederemos a `client` y vamos a instalar las dependencias, para ello utilizamos el siguiente comando:

`npm install`

Una vez instaladas las dependencias que necesita el proyecto para funcionar, ahora si vamos al siguiente paso.

### 2º Instalar paquetes
A continuacion dare una lista de dependencias que vamos a usar, la idea es de hacer un proyecto dinamico y que sea muy apetecible para el usuario, si queremos podemos instalar todo de una vez, o podemos instalar uno por uno, eso dependerá de ti, en mi caso instalaré todo de una vez.

[React Toastify](https://www.npmjs.com/package/react-toastify "Link de Documentación") 
[Sweetalert](https://www.npmjs.com/package/sweetalert "Link de Documentación")
[React Dropzone](https://www.npmjs.com/package/react-dropzone "Link de Documentación")


`npm install axios react-dropzone react-toastify reactstrap sweetalert`

Una vez que todo este listo, ya podemos ejecutar nuestro proyecto, para ello usamos el siguiente comando:

`npm run dev`

### 3º Estilos que usaremos
En nuestro proyecto vamos a usar CSS3 module, lo que basicamente es css puro de esta manera cualquiera podrá entender los estilos, nuestro proyecto solo contendrá tres componentes:
* App.jsx
* main.jsx
* UploadToCloudinary.jsx

Estos seran los estilos para cada uno:

#### Main.jsx


``` css
:root {
	--color-black: #000000;
	--color-purple: #3E065F;
	--color-lightPurple: #800B97;
	--color-lightPurple2: #8E05C2;
	--color-lightPurple3: #b05dd1;
  --color-success: #0bd41c;
  --color-failed: #c50700ee;
}


body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 100%;
  height: 100%;
  margin: 0px auto;
  padding: 0px;
  display: flex;
  flex-direction: column;
  background: linear-gradient(90deg, #009fdd,#ae00fd);

}




```


#### App.jsx

```css


.container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 30px;
  
}


.content{
  width: 50%;
  height: auto;

}

.titleMain{
  font-size: 30px;
  font-family: sans-serif,Arial, Helvetica;
  color: white;
}


```


#### UploadToCloudinary.jsx

```css
.container{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
    
}

.content{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    
}

.unloadedImage{
    width: 70%;
    height:250px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 20px;
    border-radius: 20px;
    border: 3px dotted black;
    cursor: pointer;
}

.titleUnloaded{
    font-size: 20px;
    font-family: nunito-regular;
}

.unloadedImage:hover{
    background-color: var(--color-lightPurple3);
    cursor: pointer;
    transform: scale(1.1);
    transition: all 300ms;
}


.contentImageFolder{
    width: 50px;
    height: auto;
    overflow: hidden;
}

.folderImage{
    width: 100%;
    height: 100%;
}

.parrafoFolder{
    font-size: 15px;
    font-family: nunito-regular;
}



.loading{
    width: 40%;
    height: 100px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: var(--color-lightPurple3);
    border-radius: 10px;
    box-shadow: 2px 2px 5px black;
    cursor: not-allowed;
}


.loader {
    font-size: 10px;
    width: 1em;
    height: 1em;
    border-radius: 50%;
    position: relative;
    text-indent: -9999em;
    animation: mulShdSpin 1.1s infinite ease;
    transform: translateZ(0);
  }
  @keyframes mulShdSpin {
    0%,
    100% {
      box-shadow: 0em -2.6em 0em 0em #ffffff, 1.8em -1.8em 0 0em rgba(255,255,255, 0.2), 2.5em 0em 0 0em rgba(255,255,255, 0.2), 1.75em 1.75em 0 0em rgba(255,255,255, 0.2), 0em 2.5em 0 0em rgba(255,255,255, 0.2), -1.8em 1.8em 0 0em rgba(255,255,255, 0.2), -2.6em 0em 0 0em rgba(255,255,255, 0.5), -1.8em -1.8em 0 0em rgba(255,255,255, 0.7);
    }
    12.5% {
      box-shadow: 0em -2.6em 0em 0em rgba(255,255,255, 0.7), 1.8em -1.8em 0 0em #ffffff, 2.5em 0em 0 0em rgba(255,255,255, 0.2), 1.75em 1.75em 0 0em rgba(255,255,255, 0.2), 0em 2.5em 0 0em rgba(255,255,255, 0.2), -1.8em 1.8em 0 0em rgba(255,255,255, 0.2), -2.6em 0em 0 0em rgba(255,255,255, 0.2), -1.8em -1.8em 0 0em rgba(255,255,255, 0.5);
    }
    25% {
      box-shadow: 0em -2.6em 0em 0em rgba(255,255,255, 0.5), 1.8em -1.8em 0 0em rgba(255,255,255, 0.7), 2.5em 0em 0 0em #ffffff, 1.75em 1.75em 0 0em rgba(255,255,255, 0.2), 0em 2.5em 0 0em rgba(255,255,255, 0.2), -1.8em 1.8em 0 0em rgba(255,255,255, 0.2), -2.6em 0em 0 0em rgba(255,255,255, 0.2), -1.8em -1.8em 0 0em rgba(255,255,255, 0.2);
    }
    37.5% {
      box-shadow: 0em -2.6em 0em 0em rgba(255,255,255, 0.2), 1.8em -1.8em 0 0em rgba(255,255,255, 0.5), 2.5em 0em 0 0em rgba(255,255,255, 0.7), 1.75em 1.75em 0 0em #ffffff, 0em 2.5em 0 0em rgba(255,255,255, 0.2), -1.8em 1.8em 0 0em rgba(255,255,255, 0.2), -2.6em 0em 0 0em rgba(255,255,255, 0.2), -1.8em -1.8em 0 0em rgba(255,255,255, 0.2);
    }
    50% {
      box-shadow: 0em -2.6em 0em 0em rgba(255,255,255, 0.2), 1.8em -1.8em 0 0em rgba(255,255,255, 0.2), 2.5em 0em 0 0em rgba(255,255,255, 0.5), 1.75em 1.75em 0 0em rgba(255,255,255, 0.7), 0em 2.5em 0 0em #ffffff, -1.8em 1.8em 0 0em rgba(255,255,255, 0.2), -2.6em 0em 0 0em rgba(255,255,255, 0.2), -1.8em -1.8em 0 0em rgba(255,255,255, 0.2);
    }
    62.5% {
      box-shadow: 0em -2.6em 0em 0em rgba(255,255,255, 0.2), 1.8em -1.8em 0 0em rgba(255,255,255, 0.2), 2.5em 0em 0 0em rgba(255,255,255, 0.2), 1.75em 1.75em 0 0em rgba(255,255,255, 0.5), 0em 2.5em 0 0em rgba(255,255,255, 0.7), -1.8em 1.8em 0 0em #ffffff, -2.6em 0em 0 0em rgba(255,255,255, 0.2), -1.8em -1.8em 0 0em rgba(255,255,255, 0.2);
    }
    75% {
      box-shadow: 0em -2.6em 0em 0em rgba(255,255,255, 0.2), 1.8em -1.8em 0 0em rgba(255,255,255, 0.2), 2.5em 0em 0 0em rgba(255,255,255, 0.2), 1.75em 1.75em 0 0em rgba(255,255,255, 0.2), 0em 2.5em 0 0em rgba(255,255,255, 0.5), -1.8em 1.8em 0 0em rgba(255,255,255, 0.7), -2.6em 0em 0 0em #ffffff, -1.8em -1.8em 0 0em rgba(255,255,255, 0.2);
    }
    87.5% {
      box-shadow: 0em -2.6em 0em 0em rgba(255,255,255, 0.2), 1.8em -1.8em 0 0em rgba(255,255,255, 0.2), 2.5em 0em 0 0em rgba(255,255,255, 0.2), 1.75em 1.75em 0 0em rgba(255,255,255, 0.2), 0em 2.5em 0 0em rgba(255,255,255, 0.2), -1.8em 1.8em 0 0em rgba(255,255,255, 0.5), -2.6em 0em 0 0em rgba(255,255,255, 0.7), -1.8em -1.8em 0 0em #ffffff;
    }
  }
  

.uploaded{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
    
}



.buttonStyles{
    width: auto;
    height: auto;
    padding: 10px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-content: center;
    gap: 20px;
    font-size: 20px;
    font-family: monserrat-bold;
    border: none;
    border-radius: 10px;
    background: var(--color-lightPurple);
    color: white;
    cursor: pointer;
}


.buttonStyles:hover{
    box-shadow: 2px 2px 5px var(--color-black);
    background: var(--color-lightPurple3);
    color: var(--color-black);
    transform: scale(1.1);
    transition: all 300ms;
    
}

.contentImagePreview{
    width: 800px;
    height: 400px;
    cursor: pointer;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 10px;
}

.imageUploaded{
    width: 30%;
    height: auto;
    box-shadow: 0px 2px 10px white;
}


.imageUploaded:hover{
  transform: scale(1.9);
  transition: all 300ms;
  box-shadow: none;

}


```



# Ahora que tenemos todo :smiley: vamos a programar :computer: :smile: [Vamos!!!](https://youtu.be/pGt_Di-hgJc, "Tutorial Completo")
