# Input Boxes

The built in input box component uses the provided onscreen keyboard to accept user entry for a verity of different use cases.


It can be included with Jinja using the following path:

```html
"general/input_box.html"
```

With the following parameters:

| Parameter          | Description                    | Required  | Default        |
| :---:              | :---:                          | :---:     |                |
| ```plc_symbol```   | The PLC symbol address         | ✅        | N/A            |
| ```variable_name```| The Vue.js variable name       | ✅        | N/A            |
| ```input_type```   | The type of variable to change | ✅        | N/A            |
| ```bounds```       | The PLC symbol address         | ❌        | ```Null```     |


## Supported input types

### Vue Strings

To edit javascript strings within the Vue.js app object, use the input type ```"text"``` and provide the variable that you want to access.


!!! example "Vue Strings Example"
    === "HTML"

        ``` html
        [% with
            variable_name='example_string',
            input_type="text"
        %]
            [% include "general/input_box.html" %]
        [% endwith %]
        ```

    === "Js"

        ```js
        var hmi_data = {
            data: {
                example_string: "Hello, world"
            }
        }
        ```


### Vue Numeric

To edit javascript numerical values within the Vue.js app object, use the input type ```"numeric"``` and provide the variable that you want to access.


!!! example "Vue Numeric Example"
    === "HTML"

        ``` html
        [% with
            variable_name='example_numeric',
            input_type="numeric"
        %]
            [% include "general/input_box.html" %]
        [% endwith %]
        ```

    === "Js "

        ```js 
        var hmi_data = {
            data: {
                example_numeric: 12.3
            }
        }
        ```

If the value that you are editing needs to stay within bounds just add the ```bounds``` attribute with the values that you require.

!!! example
    For example, if ```example_numeric``` cannot be lower than ```0``` or higher than ```20``` the code would be:

    === "HTML" "Vue Numeric Example With Bounds"

        ```HTML
        [% with
            variable_name='example_numeric',
            input_type="numeric",
            bounds=[0,20]
        %]
            [% include "general/input_box.html" %]
        [% endwith %]
        ```

    === "Js"

        ```js
        var hmi_data = {
            data: {
                example_numeric: 11
            }
        }
        ```


### PLC Strings

To handle PLC strings, use the input type ```"PLC_text"``` and provide the symbol that you want to access.

!!! example "PLC Strings Example"
    === "HTML"
        ```html
        [% with
            plc_symbol='GVL_HMI.G_HMI.Q.sExampleString',
            input_type="PLC_text"
        %]
            [% include "general/input_box.html" %]
        [% endwith %]
        ```


### PLC Numeric

When handling numeric values, use input type ```"PLC_numeric"``` and the library will automatically determine the type of numeric and edit accordingly. This supports all PLC numeric types, such as: ```REAL```, ```UINT```, ```INT```, etc

!!! example "PLC Numeric Example"
    === "HTML"
        ```html
        [% with
            plc_symbol='GVL_HMI.G_HMI.Q.nExampleInt',
            input_type="PLC_numeric"
        %]
            [% include "general/input_box.html" %]
        [% endwith %]
        ```


If the value that you are editing needs to stay within bounds just add the ```bounds``` attribute with the values that you require.


!!! example "Plc Numeric Example With Bounds"
    For example, if ```nExampleInt``` cannot be lower than ```0``` or higher than ```20``` the code would be:

    === "HTML"
        ```HTML 
        [% with
            plc_symbol='GVL_HMI.G_HMI.Q.nExampleInt',
            input_type="PLC_numeric",
            bounds=[0,20]
        %]
            [% include "general/input_box.html" %]
        [% endwith %]
        ```










