## Com instalar un entorn virtual

Abans de començar a treballar, hem de crear un entorn virtual en el que treballar.  Per això, obrirem la terminal del Visual Code i executarem el seguent:

- Linux: 
	- ``python3 -m venv .venv

- Windows:
	- ``python -m venv .venv

Aixó ens instala el entorn virtual a la carpeta on ens trobem. Ens he d'asegurar de que es aizi perque si no ens donara problemes més endavant. Fet aixó, aurem d'activar-lo.

- Linux:
	- ``source .venv/bin/activate
	
- Windows:
	- ``.venv\Scripts\activate

Si ho hem fet bé, veurem el seguent prompt.
**![](https://lh7-us.googleusercontent.com/LELXzxsE9YEzk-sA3Rafrq_kWwms3tdJJ32rwqf9tV1k8moaFW4bpotk3D3qoyggAw-EmpN42R3k7mD7Yw89vpd3tfUYGQ6kzyCPqdRJPqzkkMtHX49dLYQMba1mJW97XYR3VHN-fYPtOcrvJ8d8JHY)

Ara ja podem instalar els paquets necessaris per el projecte, Flask i Feedparser. Per fer-ho, escriurem a la terminal un 'pip install'.

- ``pip install flask
- ``pip install feedparser

Amb aixó ya tenim instalar l'entorn virtual. I si volem sortir escriurem:

- deactivate
## Com iniciar l'aplicatiu

1. Assegura't d'haver configurat l'entorn virtual com es descriu més amunt. 
2. A la terminal, assegura't d'estar a l'arrel del projecte. 
3. Executa la següent comanda per iniciar l'aplicació:
```
python app.py
```
Això iniciarà l'aplicació i estarà disponible a http://localhost:5000.
## Mode d'Ús

L'aplicació pot funcionar en dos modes diferents:
### Mode Remot

En aquest mode, l'aplicació obté les dades directament des de la web de La Vanguardia.

Per a usar el mode remot, no es requereix cap configuració addicional.
### Mode Local

En aquest mode, l'aplicació utilitza un arxiu XML descarregat localment per a obtenir les dades.

Per a usar el mode local, segueix aquests passos:

1. Descàrrega l'arxiu XML des d'URL de l'arxiu XML.
2. Col·loca l'arxiu descarregat en l'arrel del projecte, al costat d'app.py.

Una vegada seleccionat el mode d'ús, l'aplicació funcionarà segons la configuració proporcionada.
## Detener la Aplicación
Per aturar l'aplicació, simplement prem Ctrl + C a la terminal on s'està executant l'aplicació.
## Recursos Adicionals
- Documentació de Flask
- Documentació de [Entorns Virtuals a Python](https://docs.python.org/3/library/venv.html)

## Afegir seccions

Ens diriguim a la pagina de La Vanguardia on trobarem enllaços a diferents xml sobre un tipus de noticia. Una vegada descarregat el xml, el ficarem a la costra carpeta del rss amb les altres tres. Aixó ho farem dues vegades.

Una vegada fet, només hem d'anar al html de l'index, i afeguirem els enllaços:
![[Pasted image 20240503190142.png]]

## Navegador

Fent us del "nav", he fet un navegador ben sencill en el que es pot accedir a totes les seccions del diari. Per exmple, al fer click a "Ciencia", et portara a la pagina on es guarden totes les noticies relacionades amb la ciencia.

També he afegit una forma de retornar a la pagina originar al fer click a "La Vanguardia".

![[Pasted image 20240516171902.png]]

Aquest es el codi que he fet per crear aquest navegador:

```html
    <nav class="navbar navbar-expand-sm bg-primary navbar-dark sticky-top">
        <div class="container-fluid">
            <a class="navbar-brand" href="/">La Vanguardia</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#collapsibleNavbar">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="collapsibleNavbar">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/deportes">Deportes</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/politica">Política</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/vida">Vida</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/comer">Comer</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/ciencia">Ciencia</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
```

## Carusel

Per afegir un carousel a la meva pàgina web, vaig utilitzar el component de carousel proporcionat per Bootstrap.

Vaig seguir els següents passos per crear el carousel:

1. Vaig incloure la llibreria de Bootstrap 5.3.3 a la meva pàgina HTML mitjançant un enllaç a la seva versió distribuïda a través del CDN de Bootstrap. Aquesta llibreria és necessària per a l'ús del carousel i d'altres components de Bootstrap.
```html
 <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"

        integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
```
2. Vaig crear la estructura del carousel dins de l'element `<div>` amb l'id `carouselExampleControls`. Aquest element conté l'atribut `data-bs-ride="carousel"`, que habilita l'autoplay del carousel.
``` html
<div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
        <div class="carousel-inner">
            <div class="carousel-item active">
```
4. Dins de cada `carousel-item`, vaig incloure el contingut que volia mostrar en les diapositives. En aquest exemple, vaig utilitzar imatges placeholders amb el servei `via.placeholder.com`.
```html
<img src="../static/img/raton.jpg" class="d-block w-100 img-carousel">
```
5. Vaig afegir els controls del carousel per permetre a l'usuari navegar manualment a través de les diapositives. Aquests controls es mostren com botons de navegació a la part superior de la diapositiva.
```html
<button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleControls"
            data-bs-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleControls"
            data-bs-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
        </button>
```
    
6. Finalment, vaig incloure el JavaScript de Bootstrap al final de la pàgina per habilitar el funcionament del carousel i altres funcionalitats dinàmiques de Bootstrap.
```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
        crossorigin="anonymous"></script>
```
Amb aquests passos, vaig crear i implementar amb èxit un carousel a la meva pàgina web utilitzant Bootstrap.
## Creació d'un Layout Responsive amb Bootstrap Grid:

1. Primer, vaig incloure la llibreria de Bootstrap 5.3.3 a la pàgina HTML mitjançant un enllaç a la seva versió distribuïda a través del CDN de Bootstrap.
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
```

2. Vaig crear l'estructura bàsica de la pàgina HTML, assegurant-me que cada secció estigui dins de contenidors adequats per al grid de Bootstrap.
``` html
<!DOCTYPE html>
<html lang="ca">
<head>
    <script src="https://kit.fontawesome.com/3e4c1a6931.js" crossorigin="anonymous"></script>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>La Vanguardia - {{ rss.feed.title }}</title>
    <link rel="stylesheet" href="../static/css/style.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <style>
        .blue-header {
            background-color: blue;
            color: white;
            padding: 10px;
        }
        .card {
            margin-bottom: 20px;
        }
        .img_nav {
            height: 20px;
            width: 200px;
        }
    </style>
</head>
<body>
    <nav class="navbar navbar-expand-sm bg-primary navbar-dark sticky-top">
        <div class="container-fluid">
            <a class="navbar-brand" href="/"><img class="img_nav" src="https://www.lavanguardia.com/images/logo.png" alt="La Vanguardia Logo"></a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#collapsibleNavbar">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="collapsibleNavbar">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/deportes"><i class="fa-solid fa-football"></i> Deportes</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/politica"><i class="fa-solid fa-landmark"></i> Política</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/vida"><i class="fa-solid fa-heart"></i> Vida</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/comer"><i class="fa-solid fa-burger"></i> Comer</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="/lavanguardia/ciencia"><i class="fa-solid fa-flask"></i> Ciencia</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
    
    <div class="container">
        <h1 class="text-center blue-header">La Vanguardia - {{ rss.feed.title }}</h1>
        <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4">
            {% for item in rss.entries %}
                <div class="col">
                    <div class="card mb-3">
                        {% if item.media_content %}
                            <img src="{{ item.media_content[0].url }}" class="card-img-top" alt="{{ item.title }}">
                        {% endif %}
                        <div class="card-body">
                            <h5 class="card-title"><a href="{{ item.link }}">{{ item.title }}</a></h5>
                            <p class="card-text">Descripció: {{ item.description }}</p>
                            <p class="card-text">Data de creació: {{ item.published }}</p>
                            <p class="card-text">Data de modificació: {{ item.updated }}</p>
                            <p class="card-text">Autor: {{ item.author }}</p>
                            <p class="card-text">Categoria: {{ item.category }}</p>
                        </div>
                    </div>
                </div>
            {% endfor %}
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>
</body>
</html>
```

3. Utilitzant el sistema de grid de Bootstrap, vaig configurar la distribució del contingut perquè s'adapti automàticament segons la mida de la pantalla. Això inclou les classes `row-cols-1`, `row-cols-sm-2`, `row-cols-md-3`, i `row-cols-lg-4` per assegurar que es mostrin una, dues, tres o quatre columnes segons la mida de la pantalla.

4. Finalment, vaig verificar que el layout responia correctament a diferents mides de pantalla redimensionant la finestra del navegador i observant com es reordenaven les columnes segons les mides petites, mitjanes i grans.

## Extra
#### Icones
Per fer la pàgina més bonica, vaig posar unes icones a les diferents seccions on es podien accedir a algun tipus de notícia. Per fer-ho, vaig entrar afegir al meu codi la següent comanda:
```html
<i class="fa-solid fa-person">
```
Si afegim això en cada lloc on trobem per exemple "Deportes" entre el nom i l'enllaç ens quedarà una bonica icona a la pàgina.

![[Pasted image 20240517211430.png]]
#### Punt Avui
Al igual que hem fet amb La Vanguardia, en el app afeguim la funcio per a que s'ens mostrin les pagines rcss del Punt Avui. No ens hem d'oblidar del rss, ja que si no no funcionara.

```py
@app.route('/elpuntavui/<seccio>')
def elpuntavui(seccio):
    rss = get_rss_elpuntavui(seccio)
    return render_template("elpuntavui.html", rss = rss)

def get_rss_elpuntavui(seccio):
    xml = f"http://www.elpuntavui.cat/{seccio}.feed?type=rss"

    rss = feedparser.parse(xml)
    return rss
```

Un cop hàgim completat la tasca, prepararem el fitxer HTML per al diari Punt Avui. Per simplificar, he ajustat el codi ja existent per adaptar-lo a les seves necessitats.

Per exemple, en mostrar les imatges de les notícies, cal ajustar el codi perquè s'adeqüi a l'estructura i preferències del Punt Avui, com ara utilitzar l'atribut 'src' en lloc de 'srcset'.

Aquest ajustament implica canvis puntuals en el codi per garantir que les imatges es visualitzin correctament i s'ajustin als estàndards de presentació del Punt Avui, assegurant una experiència d'usuari òptima.

```html
<img src="{{ item.enclosures[0].href }}" class="card-img-top" alt="{{ item.title }}">
```

Amb això, només ens queda implementar una forma d'accedir a les notícies d'aquest diari. El mètode que he utilitzat consisteix a crear una taula a la pàgina inicial que mostri els diversos tipus de notícies disponibles.

Per fer-ho, he creat una taula amb diverses columnes per representar els diferents tipus de notícies, com ara notícies esportives, etc. Cada fila de la taula conté enllaços que redireccionen l'usuari a una pàgina específica dedicada a aquest tipus de notícies.

![[Pasted image 20240517212211.png]]
