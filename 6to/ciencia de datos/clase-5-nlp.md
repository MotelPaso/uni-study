# Natural Language Processing

### Terminologia
- Documentos
	Grupos de texto
- Palabras/terminos
	Texto separado con un espacio
- Corpus
	Colección de documentos
- Vocabulario/diccionario
	Conjunto de términos únicos dentro de un corpus.

### Bag of Words
Es una forma de representar cada documento como un vector de frecuencias de palabras, sin orden especifico, solo importa la frecuencia de las palabras.
### Tokenizacion
Proceso de division de un documento en unidades más pequeñas
- Divide por palabra
- Divide por oraciones
- Divide por sub palabras
- Divide por caracter
- Divide por raiz, prefijo y sufijo
#### Stopwords
Palabras "filler", sin significado demasiado importante, "el, y, en, es, un, lo" etc

### Term Frequency (TF)
La cantidad de veces que sale una palabra en el documento.

Se puede normalizar usando la siguiente formula:
$$
tf / N

$$

### Inverse Document Frecuency (IDF)
Sirve para varios documentos, pondera negativamente las palabras en proporcion a la frecuencia con la que aparecen en el conjunto de documentos.

> A menor escala, más aparece.

$$
idf_j = \ln \left(\frac{\#\ \text{documents}}{\#\ \text{documents with word j}}\right)
$$

