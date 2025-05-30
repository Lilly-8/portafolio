+++
date = '2025-05-26T20:27:37-07:00'
draft = false
title = 'Practica 0: Uso de repositorios'
weight = 1
+++

---

## Introducción

En esta práctica aprendimos los fundamentos de Markdown, Git, GitHub, Hugo y GitHub Actions para crear una página estática. Esta actividad se dividió en tres sesiones, cada una con objetivos específicos que se integran para formar un portafolio digital automatizado.

---

## Primera sesión: Markdown

### ¿Qué es Markdown?

Markdown es un lenguaje de marcado ligero que permite crear contenido con formato utilizando una sintaxis sencilla. Es ampliamente usado en documentación, archivos README, blogs estáticos, entre otros.

### ¿Cómo se utiliza?

Markdown se escribe en archivos con la extensión `.md`. Permite aplicar estilos como **negritas**, *cursivas*, `código`, listas, encabezados, enlaces e imágenes.

### Sintaxis básica

markdown

# Título nivel 1

## Título nivel 2

### Título nivel 3

**Negritas**  
*Cursivas*  
\`Código\`  

- Lista
- No ordenada

1. Lista
2. Ordenada

---

## Segunda sesión: Git y GitHub

### ¿Qué es Git?

Git es un sistema de control de versiones distribuido que permite registrar y gestionar cambios en archivos de forma eficiente y colaborativa.

### ¿Qué es GitHub?

GitHub es una plataforma en la nube que aloja repositorios Git, permitiendo la colaboración y publicación de proyectos.

### Comandos esenciales de Git

- git init                    *# Inicializa un repositorio*  
- git clone URL               *# Clona un repositorio remoto*  
- git status                  *# Muestra los archivos modificados*  
- git add .                   *# Agrega todos los archivos al staging area*  
- git commit -m "mensaje"     *# Guarda los cambios con un mensaje*  
- git push origin main        *# Sube los cambios al repositorio remoto*  
- git pull origin main        *# Descarga los cambios del repositorio remoto*

### ¿Cómo crear un repositorio y subir archivos?

1. Crear cuenta en [GitHub](https://github.com/)
2. Crear un nuevo repositorio desde la interfaz web.
3. En la terminal:

bash
git init  
git remote add origin <https://github.com/Lilly-8?tab=repositories>  
git commit -m "Primer commit"  
git push -u origin main

---

## Tercera sesión: Hugo y GitHub Actions

### ¿Qué es Hugo?

Hugo es un generador de sitios estáticos muy rápido y flexible. Permite crear páginas web usando Markdown, y genera el contenido como HTML.

### ¿Qué es GitHub Actions?

GitHub Actions permite automatizar flujos de trabajo. En este caso, se utiliza para desplegar automáticamente el sitio generado con Hugo a GitHub Pages.

### Crear un sitio estático con Hugo

1. Instalar Hugo desde: [https://gohugo.io/getting-started/installing/](https://gohugo.io/getting-started/installing/)

2. Crear un nuevo sitio:

```Prolog
hugo new site mi-portafolio
cd mi-portafolio
git init
```

1. Descargar un tema:

```Prolog
git submodule add <https://github.com/theNewDynamic/gohugo-theme-ananke.git> themes/ananke
echo 'theme = "ananke"' >> config.toml
```

4. Crear contenido:

```Prolog
hugo new posts/practica0.md
```

5. Compilar y ver el sitio local:

```Prolog
hugo server
```

6. Construir el sitio:

```Prolog
hugo
```

### Publicar con GitHub Pages y GitHub Actions

1. Crear un repositorio en GitHub llamado `mi-portafolio`.
   
2. Subir el sitio generado (`/public`) a una rama llamada `gh-pages`.
   
3. Crear un archivo `.github/workflows/deploy.yml` con el siguiente contenido:

yaml  
name: Deploy Hugo site to GitHub Pages

```Prolog
on:  
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v3

    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: 'latest'

    - name: Build
      run: hugo --minify

    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./public
```

4. Habilitar GitHub Pages desde la configuración del repositorio seleccionando la rama `gh-pages`.

---

## Enlaces del portafolio

- Repositorio del portafolio: [https://github.com/Lilly-8/portafolio](https://github.com/Lilly-8/portafolio)
- Página estática en GitHub Pages: [https://lilly-8.github.io/portafolio/](https://lilly-8.github.io/portafolio/)

---

## Conversión a PDF

Para convertir este archivo Markdown a PDF puedes usar alguna de las siguientes herramientas:

- Extensión de VS Code: "Markdown PDF"
- Pandoc (desde terminal):  

```Prolog
  pandoc reporte.md -o reporte.pdf
```

---

## Conclusión

Esta práctica fue una introducción esencial al uso de herramientas modernas para la creación de portafolios y proyectos colaborativos. Aprendí a utilizar Markdown para documentar, Git y GitHub para versionar y compartir mi código, y Hugo junto con GitHub Actions para automatizar la publicación de páginas estáticas. Estos conocimientos me serán útiles tanto en futuros cursos como en el entorno profesional.

♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡
<!-- esto es un comentario--> 

# Encabezado 1
## Enabezado 2
### Encabezado 3
#### Encabezado 4 
##### Encabezado 5

<!-- Italicas -->
Este es un texto en *italicas*

Este es un texto en _italicas_

<!-- Negritas -->
Este es un texto en **negritas**

Este es un texto en __negritas__

<!-- Rayado -->
Este es un texto ~~rayado~~

<!-- UL -->

* Elemento 1
* Elemento 2
* Elemento 3
  * Elemento 3.1
  * Elemento 3.2
* Elemento 4

<!-- OL -->
1. Elemento 1
2. Elemento 2
3. Elemento 3
   1. Elemento 3.1
   2. Elemento 3.2
4. Elemento 4

<!-- Enlaces -->
[UABC](www.uabc.mx)

[UABC](www.uabc.mx "Titulo personalizado")

<!-- Imagenes -->
![Logo UABC](https://citecuvp.tij.uabc.mx/wp-content/uploads/2022/10/07_ESCUDO-UABC-DOS-COLRES_1.png) 

![Logo UABC](./cimarron.png "CIMARRONES CON VALORES")

![Logo UABC](./cimarronX.png "CIMARRONES CON VALORES")

<img src="./escudo_uabc.png" alt="cimarron" width="150" height="auto"> 

[<img src="./escudo_uabc.png" alt="cimarron" width="150" height="auto"> ]()

<!-- Bloques de codigo -->
```
This is a code block
This is the second line of the code block
```

```python
print("Hello World!")
```

```javascript
console.long("Hello world")

const test = ()
```

```HTML
<h1>Hello World!</h1>
```

<!-- Tablas -->
| Productos | Precio | Cantidad |
| --- | --- | --- | 
| Laptop | 3.33 | 2 |
| Mouse | 10.33 | 1 |

| Productos | Precio | Cantidad |
| --------- | ------ | -------- | 
| Laptop    | 3.33   | 2        |
| Mouse     | 10.33  | 1        |

<!-- Tareas -->
* [x] Primera Tarea
* [ ] Segunda Tarea 
* [ ] Tercera Tarea
* [x] Cuarta Tarea

<!-- Menciones -->
♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡♡