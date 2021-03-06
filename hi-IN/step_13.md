## हमें वेब सर्वर चलाने की आवश्यकता क्यों थी?

हमें वेब सर्वर के माध्यम से हमारा वेबपेज __serve__ करना था ताकि हम JSON डेटा को प्रोसेस कर सकें।

जब डेटा को वेब पर होस्ट किया जाता है, तो वेब सर्वर को सावधान रहना होगा कि वे हैकर्स से हमलों के लिए खुद डेटा को न खोलें। आपने क्रॉस-साइट स्क्रिप्टिंग हमलों (या शॉर्ट के लिए XSS) के बारे में चेतावनी देखी होगी, जो हैकर्स को सामान्य वेबसाइटों पर अपना दुर्भावनापूर्ण कोड डालने की अनुमति दे सकते हैं। ऐसा होने से रोकने के लिए, वेब ब्राउज़र **समान मूल नीति**संचालित करते हैं, जिसका अर्थ है कि वेबपेज 1 पर कोड केवल वेबपेज 2 के डेटा का उपयोग कर सकता है यदि दोनों पृष्ठ एक ही मूल के हैं (जिसका अर्थ है मोटे तौर पर "एक ही सर्वर पर होस्ट किया जाता है")।

तो अब हमारे पास एक समस्या है। हम चाहते हैं कि हमारा वेब पेज JSON डेटा एक्सेस करे, लेकिन हमारी स्क्रिप्ट डेटा वाले सर्वर पर नहीं चल रही होगी।

**मैं सिर्फ डेटा स्रोत से JSON फ़ाइल को डाउनलोड क्यों नहीं कर सकता और इसे अपने कंप्यूटर पर फ़ाइल के रूप में एक्सेस क्यों नहीं कर सकता हूं?**

जब आप अपने वेबपेज को केवल वेब ब्राउज़र में खोलकर देखेंगे, तो पता `file://` से शुरू होगा, जैसे कि JSON फ़ाइल होगी यदि यह आपके कंप्यूटर पर सहेजी गई है।

  ![ब्राउज़र में फ़ाइल खोलें](images/file-in-browser.png)

सुरक्षा कारणों से, JavaScript आपको स्थानीय(Local) फ़ाइलों (एक ही कंप्यूटर पर फ़ाइलें) का उपयोग करने की अनुमति नहीं देता है, इसलिए यह काम नहीं करेगा।

**फिक्स - JSON फ़ाइल डाउनलोड करें और इसे एक स्थानीय(Local) वेब सर्वर के माध्यम से सेवा दें**

यह वह मेथड है जिसका हमने उपयोग किया था, और यहाँ है यह क्यों काम करता है। सरल Python वेब सर्वर चलाकर, आप अपने कंप्यूटर को अपने वेब ब्राउज़र के पेज को "serve" कर रहे हैं। जब आप `http://localhost:8000`पर जाते हैं ऐसा लगता है आप किसी वास्तविक वेबसाइट पर जाते हैं, - आप एक सर्वर से एक अनुरोध कर रहे हैं, जो तब आपके द्वारा मांगे गए पेज को वापस भेज देता है।

यदि आप अपना `index.html` फ़ाइल अपने वेब सर्वर पर डालते हैं, और फिर इसे `http://localhost:8000/index.htm` के रूप में एक्सेस करते हैं, इसका **origin** `http://localhost:8000` है। यदि आप अपनी JSON फाइल को वेब सर्वर के माध्यम से भी भेजते हैं, तो इसे `http://localhost:8000/penalties.json` पर एक्सेस किया जा सकता है। और इसलिए इसका **origin** __भी__ `http://localhost:8000` है। यह उसी मूल नियम को संतुष्ट करता है, और इसलिए हम अपने JavaScript में JSON डेटा तक पहुंचने में सक्षम हैं!

संयोग से, JSON डेटा की पेशकश करने वाले कुछ वेब सर्वर एक विशेष हेडर भेजने के लिए अलग-अलग मूल से पहुंचने की अनुमति देते हैं। इस संसाधन में उपयोग किए गए डेटा वाले सर्वर में यह सेट-अप नहीं है, इसलिए हमने फ़ाइल डाउनलोड की और इसे स्थानीय रूप से सेवा दी।


