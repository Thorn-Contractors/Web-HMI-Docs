```
# HmiInputBox Component

The built-in HmiInputBox Vue component provides a customizable input box that supports different use cases including string and numeric inputs.

You can use this component in your Vue template as follows:

```html
<hmi-input-box/>
```

Below are the prop details:

| Prop              | Description                    | Required  | Default        |
| :---:             | :---:                          | :---:     |                |
| ```inputType```   | The type of input to accept    | ✅        | ```"text"```   |
| ```variable```    | The Vue.js variable name       | ❌        | ```""```       |
| ```plcSymbol```   | The PLC symbol address         | ❌        | ```""```       |
| ```bounds```      | Bounds for numeric input       | ❌        | ```undefined```|
| ```decimalPlaces```| Number of decimal places for the numeric input | ❌ | ```undefined``` |

## Supported input types

### Vue Strings

To edit JavaScript strings within the Vue.js app object, use the prop `inputType` with value `"text"` and provide the variable that you want to access.


!!! example "Vue Strings Example"
    === "HTML"

        ``` html
        <hmi-input-box
            input-type="text"
            variable="exampleString"
        />
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

To edit JavaScript numerical values within the Vue.js app object, use the prop `inputType` with value `"numeric"` and provide the variable that you want to access.


!!! example "Vue Numeric Example"
    === "HTML"

        ``` html
        <hmi-input-box
            input-type="numeric"
            variable="exampleNumeric"
        />
        ```

    === "Js"

        ```js
        var hmi_data = {
            data: {
                exampleNumeric: 12.3
            }
        }
        ```

If the value that you are editing needs to stay within bounds, add the `bounds` prop with the values that you require.


!!! example "Vue Numeric Bounds Example"
    === "HTML"

        ``` html
        <hmi-input-box
            input-type="numeric"
            variable="exampleNumeric"
            :bounds="[0, 20]"
        />
        ```

    === "Js"

        ```js
        var hmi_data = {
            data: {
                exampleNumeric: 11
            }
        }
        ```


### PLC Strings

To handle PLC strings, use the prop `inputType` with value `"PLC_text"` and provide the symbol that you want to access.


!!! example "PLC Strings Example"
    === "HTML"

        ``` html
        <hmi-input-box
            input-type="PLC_text"
            plcSymbol="GVL_HMI.G_HMI.Q.sExampleString"
        />
        ```

### PLC Numeric

To handle numeric values from a PLC, use the prop `inputType` with value `"PLC_numeric"`. This supports all PLC numeric types, such as: `REAL`, `UINT`, `INT`, etc.

!!! example "PLC Numeric Example"
    === "HTML"

        ``` html
        <hmi-input-box
            input-type="PLC_numeric"
            plcSymbol="GVL_HMI.G_HMI.Q.nExampleInt"
        />
        ```

If the value that you are editing needs to stay within bounds, add the `bounds` prop with the values that you require.


!!! example "PLC Numeric Bounds Example"
    === "HTML"

        ``` html
        <hmi-input-box
            input-type="PLC_numeric"
            plcSymbol="GVL_HMI.G_HMI.Q.nExampleInt"
            :bounds="[0, 20]"
        />
        ```
