# Java Coding Challenge: XML to JSON Converter

Write a Java class that converts XML to JSON, according to a set of mapping rules.

## Specifications

You may name your class however you like, and may design whatever API makes sense to you,
provided that you meet the following specifications.

An instance of the converter class is given a character input stream and a character output
stream, parses XML from the input stream, and writes equivalent JSON to the output stream.

To generate JSON, the converter class obeys the following rules by default:

- All XML namespaces are ignored.
- Each XML element is converted to a JSON object.  The _tag property of the JSON object is set to the XML tag name (a String).
- The root XML element is equivalent to the root JSON object.
- For each child XML element, the equivalent JSON object is added to an array, which is a property of the parent JSON object.  The name of the property is the same as the element tag.  All child elements having the same parent and the same tag name are reflected by equivelent JSON objects in a single list.  The order in which the JSON object appear in the list is the order in which the equivalent XML elements appear in the document.
- For each child XML text node, the text string is added to an array, which appears as the _text property of the parent JSON object.  The text is trimmed of leading and trailing whitespace.
- Each XML attribute is converted to a String property in the equivalent JSON object.  
- If a child element and an attribute of an XML element have the same name, the attribute value is masked (discarded).
- In the case of an XML parse exception, the converter an exception is thrown by the converter and *no* JSON output is written
- The converter always outputs valid JSON!

### Example:

Input:

```
<?xml version="1.0"?>
<recipe version="1.0" xmlns="http://swoop.com/1.0">
	<title>Moroccan Lentils and Couscous</title>
	<description>
		Yum, yum.
	</description>
	<ingredient ref="/library/lentil-258">1 cup lentils, uncooked</ingredient>
	<ingredient>4 garlic cloves, crushed</ingredient>
	<ingredient>1 teaspoon cumin, ground</ingredient>
	<ingredient>1/2 teaspoon salt</ingredient>
	<ingredient>1/8 teaspoon pepper</ingredient>
	<ingredient>1/16 teaspoon ground cinnamon</ingredient>
	<ingredient>1 bay leaf</ingredient>
	<ingredient>3 cups water</ingredient>
	<ingredient>2 teaspoons vegetable oil</ingredient>
	<ingredient>2 cups onions, cut in thin slices</ingredient>
	<ingredient ref="/library/couscous-19">1/2 cup couscous, uncooked</ingredient>
	<directions>
		Mix everything together and microwave for 5 minutes.
	</directions>
</recipe>
```

Output: (formatting details in your output may differ!)

```
{
	"version": "1.0",
	"title": {
		"_tag": "title",
		"_text": "Moroccan Lentils and Couscous",
	},
	"description": {
		"_tag": "description",
		"_text": "Yum, yum."
	},
	"ingredient": [{
		"_tag": "ingredient",
		"ref": "/library/lentil-258",
		"_text": "1 cup lentils, uncooked"
	},{
		"_tag": "ingredient",
		"_text": "4 garlic cloves, crushed"
	},{
		"_tag": "ingredient",
		"_text": "1 teaspoon cumin, ground"
	},{
		"_tag": "ingredient",
		"_text": "1/2 teaspoon salt"
	},{
		"_tag": "ingredient",
		"_text": "1/8 teaspoon pepper"
	},{
		"_tag": "ingredient",
		"_text": "1/16 teaspoon ground cinnamon"
	},{
		"_tag": "ingredient",
		"_text": "1 bay leaf</ingredient>
	},{
		"_tag": "ingredient",
		"_text": "3 cups water</ingredient>
	},{
		"_tag": "ingredient",
		"_text": "2 teaspoons vegetable oil</ingredient>
	},{
		"_tag": "ingredient",
		"_text": "2 cups onions, cut in thin slices</ingredient>
	},{
		"_tag": "ingredient",
		"ref": "/library/couscous-19",
		"_text": "1/2 cup couscous, uncooked"
	}],
	"directions": {
		"_tag": "directions",
		"_text": [ "Mix everything together and microwave for 5 minutes." ]
	}
}
```

## Submission

Please submit a link to the public github repository that contains your code.  Please include any build files
(maven, ant, or make), supporting scripts and documentation in the repository.  As we will want to run your code
to check for correctness, you must include some sort of test driver.

