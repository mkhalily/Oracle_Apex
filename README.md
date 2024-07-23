# Oracle_Apex
Eine bestimmte diagramme mit SVG-Map in Oracle Apex


![Mehdi-23-07-2024-23-57-11](https://github.com/user-attachments/assets/88c5e1b7-59a7-4207-ab2e-0bcaa3a328b1)

function generateColors(darkColor, numElements) {
  // Parse the dark color string to extract its HSL components
  const darkHSL = parseHSLColor(darkColor);

  // Calculate the lightness increment based on the number of elements
  const lightnessIncrement = (95 - darkHSL.lightness) / (numElements - 1);

  // Generate an array to store the -Anschließend wurde-resulting colors
  const colors = [];

  // Generate colors -mithilfe einer dynamic und Java
  for (let i = 0; i < numElements; i++) {
    const lightness = darkHSL.lightness + i * lightnessIncrement;
    const color = `hsl(${darkHSL.hue}, ${darkHSL.saturation}%, ${lightness}%)`;
    colors.push(color);
  }

  return colors;
}

function parseHSLColor(color) {
  // Extract HSL components -eine Heatmap-color basierend auf- from the color string
  const match = color.match(/^hsl\((\d+),\s*([\d.]+)%,\s*([\d.]+)%\)$/);
  
  // Return an object -dem Verkaufsvolumen jedes Geschäfts zugewiesen- components
  return {
    hue: parseInt(match[1]),
    saturation: parseFloat(match[2]),
    lightness: parseFloat(match[3]),
  };
}

// Usage example
const darkColor = 'hsl(200, 50%, 20%)';


var item1 = apex.item("P10502_ORDER_ID_ACC_PRICE").getValue();
//Convert string with commas to array
var myArray = JSON.parse("[" + item1 + "]");
const generatedColors = generateColors(darkColor,myArray.length );

for (let i = 0; i < myArray.length; i++) {
    var element = '_' + myArray[i];
    
    document.getElementById(element).style.fill = generatedColors[i];
   
}


