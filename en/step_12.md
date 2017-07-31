## Adding more data

- Now that we have access to all the JSON data, we can also plot some of the other data at each data point. Locate the line `icon: emoji`. Add a comma at the end of the line so that we can add another parameter on the line below.

- Add a line below to plot the description of the penalty on the data marker:

    ```JavaScript
    icon: emoji,
    title: data[i]["Contravention_Description"]
    ```

- Refresh your map. When you hover your mouse over one of the icons, you will see the type of penalty appear in a tooltip.

    ![Leaving litter](images/leaving-litter.png)


