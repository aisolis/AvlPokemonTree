
## Métodos para el uso de la api

### `[POST] /Upload`

Lee un archivo csv proporcionado por el usuario y los añade a un diccionario de datos don los pokemons correspondientes.

Expuesto en: 
**Link:** https://avlpokemontree.onrender.com/upload
**Metodo:** [POST]
**Body postman:** 
 - Type form-data,
 - key='file'
 -  Value= file.cs

El formato del csv es el siguiente:

| Nombre     | Nivel | Tipo      |
|------------|-------|-----------|
| Pikachu    | 5     | Eléctrico |
| Charmander | 5     | Fuego     |
| Bulbasaur  | 5     | Planta    |

Manteniendo el encabezado 
| Nombre     | Nivel | Tipo      |
|------------|-------|-----------|

El balanceo del arbol AVL se realizara en base al orden alfabetico de los pokemons

-   **Parámetros:**
    
    -   `file`:  Sera el archivo csv que contendra los pokemons a agregar

### curl
  
```bash 
curl --location 'https://avlpokemontree.onrender.com/upload' \
--form 'file=prueba.csv"'
```
![LLenar lista de pokemones](/images/postImage.PNG)

### Output
```json
[
    {
        "Nivel": 5,
        "Nombre": "pikachu",
        "Tipo": "electrico"
    },
    {
        "Nivel": 99,
        "Nombre": "arceus",
        "Tipo": "psiquico"
    },
    {
        "Nivel": 67,
        "Nombre": "charmander",
        "Tipo": "fuego"
    },
    {
        "Nivel": 50,
        "Nombre": "bulbasaur",
        "Tipo": "planta"
    }
]
```

### `[GET] /search?name={PkmName}`
Este metodo se utiliza para buscar un pokemon en especifico por su nombre dentro del arbol AVL

-   **Parámetros:**
`PkmnName:`  Es el nombre del pokemon a buscar dentro del listado este se pasa por **PATHPARAM**

### curl
  
```bash 
curl --location 'https://avlpokemontree.onrender.com/search?name=pikachu'
```
![Obtener lista de pokemones](/images/allPkms.PNG)

### Output
```json
[
	{
	"Nivel":  5,
	"Nombre":  "pikachu",
	"Tipo":  "electrico"
	}
]
```

### `[GET] /pokemons`

Obtiene un listado de todos los Pokémon's cargados al diccionario
### curl
  
```bash 
curl --location 'https://avlpokemontree.onrender.com/pokemons'
```
![Obtener lista de pokemones](/images/pokemons.PNG)

### Output
```json
[
    {
        "Nivel": 5,
        "Nombre": "pikachu",
        "Tipo": "electrico"
    },
    {
        "Nivel": 99,
        "Nombre": "arceus",
        "Tipo": "psiquico"
    },
    {
        "Nivel": 67,
        "Nombre": "charmander",
        "Tipo": "fuego"
    },
    {
        "Nivel": 50,
        "Nombre": "bulbasaur",
        "Tipo": "planta"
    }
]
```
### `[POST] /pokemon`

Este metodo sirve para añadir pokemons al diccionario y al arbol AVL

Expuesto en: 
**Link:** https://avlpokemontree.onrender.com/add_pokemon
**Metodo:** [POST]
**Body postman:** 
- **Type:** Json
- **Body**:
```json
{
	"Nivel":  100,
	"Nombre":  "umbreon",
	"Tipo":  "Siniestro"
}
```

### curl
  
```bash 
curl --location curl --location 'https://avlpokemontree.onrender.com/pokemon' \
--header 'Content-Type: application/json' \
--data '{
    "Nivel": 100,
    "Nombre": "umbreon",
    "Tipo": "Siniestro"
}'
```
![Obtener lista de pokemones](/images/addPokm.PNG)

### Output
```json
{
	"mensaje":  "Pokémon agregado con éxito",
	"pokemon":  {
	"Nivel":  100,
	"Nombre":  "umbreon",
	"Tipo":  "Siniestro"
	}
}
```