## Get a Google maps API key

Next, you'll need to create a Google Maps API key. An API (or Application Programming Interface) is a set of functions provided so that you can interact with another computer - in this case the Google Maps server. You need to have an **API key** to access it, so that Google knows who it has allowed to use its services.

- Open [this page](https://developers.google.com/maps/documentation/javascript/adding-a-google-map#step_3_get_an_api_key) and, under the heading "Step 3: Get an API key", follow the steps to obtain a Google Maps JavaScript API key.

  **Note - using the API is free but you will need a credit/debit card to complete the sign up.**

- Go back to your `index.html` file and position your cursor just before the `</body>` tag. Paste in the code below:

    ```html
    <script async defer
      src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap">
    </script>
    ```

- Locate the part in the code you just pasted which says `YOUR_API_KEY` and replace it with the API key you just generated, making sure there are no spaces between the key you paste in and the `=` and `&` characters on each side of it.

