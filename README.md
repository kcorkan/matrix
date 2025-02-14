# Matrix
This HTML snippet is a simple but effective way to create a dynamic and interactive grid visualization of data from a Rally API. 

In the absence of a settings panel, the settings are provided in the code **config** object which defined the configuration and variables for the grid.   

In summary, this HTML snippet uses Grid.js to visualize Rally data. It dynamically fetches data from the Rally API, processes it, and creates a grid view based on the configured settings and filters. This allows users to interact with and explore Rally data in a user-friendly grid format.

# Technical Notes  

### **config** object: 
* type: Specifies the type of Rally object to fetch (in this case, "Defect").
* xAxis and yAxis: Define the x and y axes of the grid based on Rally object fields. For example, "State" for the x-axis and "Project.Name" for the y-axis.
* yAxisLabel: Sets the label for the y-axis.
* includeBlanks, includeRowTotals, includeColTotals: Determines if blank cells, row totals, and column totals should be included in the grid.
* sortAlpha, ¨C19C: Configures sorting options for the grid.
* TBD: Controls the maximum number of rows and page size for fetching data.
* TBD: Specifies the fields to fetch from the Rally API.
* TBD: Defines the Rally query to filter the data.

```<script>$RallyContext:Begin // $RallyContext:End </script> ``` This is a placeholder for Rally context data.  Contextual data is dynamically injected by within the Rally environment.

``` var config = { ... }; ... var url = ...; var matrix = []; ... :``` 

### JavaScript for Data Fetching and Grid Creation:

if ($RallyContext.ViewFilter.Type == 'Release'){ ... } and if ($RallyContext.ViewFilter.Type == 'Iteration'){ ... }: These blocks dynamically update the query based on the currently active Rally view filter. If the filter is "Release," the query targets defects associated with that release. If it's "Iteration," the query filters for defects within the current iteration.

url variable: Constructs the URL for the Rally API request based on the config object and the Rally context.

matrix, columns, rows: These variables are used to store the data for the grid as it's processed.

```fetch(url)```: This line makes a fetch request to the Rally API using the constructed URL. It fetches data based on the specified query, fields, and filters.

```.then(response => {return response.json()})```: This part handles the response from the API. It parses the JSON data returned by the API and passes it to the next then block.

```.then(queryResult => { ... })```: This block processes the data fetched from Rally. The code iterates through the returned defects (queryResult.QueryResult.Results) and populates the matrix, columns, and rows variables. This creates a matrix structure that represents the data for the grid.

```const grid = new gridjs.Grid({ ... }).render(document.getElementById("wrapper"));```: This code uses the Grid.js library to create a new grid instance. It passes the columns and data derived from the Rally data to the grid, then renders the grid inside the "wrapper" div in the HTML.

  
