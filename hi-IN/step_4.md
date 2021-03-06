## Google Map एपीआई (API) Key प्राप्त करें

इसके बाद, आपको Google Map एपीआई(API) की कुंजी बनाने की आवश्यकता होगी। एक एपीआई (या एप्लिकेशन प्रोग्रामिंग इंटरफ़ेस) प्रदान किए गए कार्यों का एक सेट है, ताकि आप किसी अन्य कंप्यूटर के साथ बातचीत कर सकें - इस मामले में Google Map सर्वर। इसे एक्सेस करने के लिए आपके पास **API key** होना आवश्यक है ताकि Google को पता हो कि उसने अपनी सेवाओं का उपयोग करने की अनुमति किसको दी है।

- "Step 3: Get an API key" शीर्षक के तहत,[this page](https://developers.google.com/maps/documentation/javascript/adding-a-google-map#step_3_get_an_api_key)को खोलें और, Google Map JavaScript एपीआई कुंजी प्राप्त करने के लिए चरणो का पालन करें।

  **नोट - एपीआई(API) का उपयोग करना नि: शुल्क है लेकिन साइन अप को पूरा करने के लिए आपको क्रेडिट / डेबिट कार्ड की आवश्यकता होगी।**

- अपने `index.html` पर वापस जाएं `</body>` टैग के ठीक पहले अपने कर्सर को वहाँ पहुचाये। नीचे दिए गए कोड में पेस्ट करें:

    ```html
    <script async defer
      src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap">
    </script>
    ```

- जिस कोड को आप पेस्ट करते हैं उसमें उस भाग का पता लगाएँ जो कहता है `Your_API_KEY` और इसे केवल आपके द्वारा बनाई गई API कुंजी से बदल दें, सुनिश्चित करें कि आपके द्वारा पेस्ट की गई कुंजी के बीच कोई रिक्त स्थान नहीं है और `=` और `&` इसके हर तरफ मौजूद है ।

