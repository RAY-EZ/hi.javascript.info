# Hello, world! (नमस्ते दुनिया!)

शिक्षण जो आप पढ़ रहे हैं, वह कोर जावास्क्रिप्ट के बारे में है, जो प्लेटफ़ॉर्म-स्वतंत्र है। इसके अलावा, आप Node.JS और इसका उपयोग करने वाले अन्य प्लेटफ़ॉर्म सीखेंगे।

लेकिन, हमें अपनी स्क्रिप्ट को चलाने के लिए काम करने का environment चाहिए, और, सिर्फ इसलिए कि यह पुस्तक ऑनलाइन है, ब्राउज़र एक अच्छा विकल्प है। हम ब्राउज़र-विशिष्ट commands की मात्रा कम रखेंगे (जैसे `alert`) ताकि, यदि आप किसी अन्य environment जैसे Node.JS पर ध्यान केंद्रित करने की योजना बनाते हैं, तब आप ब्राउज़र जावास्क्रिप्ट सीखने में समय व्यतीत नहीं करेंगे। हम ट्यूटोरियल के [अगले भाग](/ui) में ब्राउज़र जावास्क्रिप्ट पर ध्यान केंद्रित करेंगे।

तो पहले यह देखते हैं कि हम किसी स्क्रिप्ट को वेबपेज से कैसे जोड़ते हैं। सर्वर-साइड वातावरण (जैसे Node.js) के लिए, आप स्क्रिप्ट को `"node my.js"` जैसे कमांड से निष्पादित कर सकते हैं।

## "स्क्रिप्ट" टैग

जावास्क्रिप्ट प्रोग्रामों को HTML दस्तावेज़ के किसी भी भाग में `<script>` टैग की सहायता से डाला जा सकता है।

उदाहरण के लिए:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>स्क्रिप्ट से पहले...</p>

*!*
  <script>
    alert( 'Hello, world!' );
  </script>
*/!*

  <p>...स्क्रिप्ट के बाद.</p>

</body>

</html>
```

```online
आप ऊपर दिए गए बॉक्स के दाएं-कोने में "प्ले" बटन पर क्लिक करके उदाहरण चला सकते हैं।
```

`<स्क्रिप्ट>` टैग में जावास्क्रिप्ट कोड होता है जो ब्राउज़र द्वारा टैग को संसाधित (process) करने पर स्वचालित रूप से निष्पादित होता है।

## आधुनिक मार्कअप (markup)

`<स्क्रिप्ट>` टैग में कुछ attributes (विशेषताएं) हैं जो आजकल शायद ही कभी उपयोग की जाती हैं, लेकिन अभी भी पुराने कोड में पाई जा सकती हैं:

`type` attribute: <code>&lt;script <u>type</u>=...&gt;</code>
: पुराने HTML संस्करण, HTML4 में स्क्रिप्ट में एका attribute `type` की आवश्यकता होती है। `type`. आमतौर पर यह `type="text/javascript"` था. इसकी अब आवश्यकता नहीं है। साथ ही, आधुनिक HTML मानक ने इस विशेषता के अर्थ को पूरी तरह से बदल दिया है। अब, इसका उपयोग जावास्क्रिप्ट मॉड्यूल के लिए किया जा सकता है। लेकिन यह एक उन्नत विषय है, हम ट्यूटोरियल के दूसरे भाग में मॉड्यूल के बारे में बात करेंगे।

`language` attribute: <code>&lt;script <u>language</u>=...&gt;</code>
: यह attribute स्क्रिप्ट की भाषा दिखाने के लिए थी। यह attribute अब मायने नहीं रखती है क्योंकि जावास्क्रिप्ट डिफ़ॉल्ट भाषा है। इसका उपयोग करने की कोई आवश्यकता नहीं है।

स्क्रिप्ट से पहले और बाद की टिप्पणियाँ।
: वास्तव में पुरानी किताबों और गाइडों में, आप इस तरह से `<स्क्रिप्ट> टैग के अंदर टिप्पणी पा सकते हैं:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    इस तकनीक का उपयोग आधुनिक जावास्क्रिप्ट में नहीं किया जाता है। ये टिप्पणियां जावास्क्रिप्ट कोड को उन पुराने ब्राउज़रों से छिपाती हैं, जो '<स्क्रिप्ट>' टैग को प्रोसेस करना नहीं जानते थे। चूंकि पिछले 15 वर्षों में जारी किए गए ब्राउज़रों में यह समस्या नहीं है, इसलिए इस तरह की टिप्पणी से आप वास्तव में पुराने कोड को पहचान सकते हैं।


## बाहरी स्क्रिप्ट

यदि हमारे पास बहुत अधिक जावास्क्रिप्ट कोड है, तो हम इसे एक अलग फाइल में डाल सकते हैं।

स्क्रिप्ट फाइलें HTML से `src` विशेषता के साथ जुड़ी हुई हैं:

```html
<script src="/path/to/script.js"></script>
```

यहाँ, `/path/to/script.js` यह साइट रूट से स्क्रिप्ट के लिए एक absolute (निरपेक्ष) पथ है। वर्तमान पृष्ठ से कोई एक relative (आपेक्षिक) पथ भी प्रदान कर सकता है। उदाहरण के लिए, `src="script.js"` वर्तमान फोल्डर के अंदर एक फ़ाइल `"script.js"` का अर्थ होगा।

हम एक पूर्ण URL भी दे सकते हैं। उदाहरण के लिए:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

कई स्क्रिप्ट संलग्न करने के लिए, कई टैग का उपयोग करें:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
एक नियम के रूप में, केवल सरलतम स्क्रिप्ट HTML में डाली जाती हैं। अधिक जटिल अलग फ़ाइलों में रहते हैं।

एक अलग फ़ाइल का लाभ यह है कि ब्राउज़र इसे डाउनलोड करेगा और इसे अपने कैश में रखेगा [cache](https://en.wikipedia.org/wiki/Web_cache).

उसी स्क्रिप्ट को संदर्भित करने वाले अन्य पृष्ठ इसे डाउनलोड करने के बजाय इसे कैश से ले लेंगे, इसलिए फ़ाइल वास्तव में केवल एक बार डाउनलोड की जाती है।

यह ट्रैफ़िक कम करता है और पृष्ठों को तेज़ बनाता है।
```

````warn header="यदि `src` सेट है, तो स्क्रिप्ट के अंदर मौजूद कोड को अनदेखा कर दिया जाता है।"
एक <script> `टैग के अंदर` src` attribute और कोड दोनों नहीं हो सकते।

यह काम नहीं करेगा:

```html
<script *!*src*/!*="file.js">
  alert(1); // इस कोड को अनदेखा कर दिया जाएगा, क्योंकि src सेट है
</script>
```

हमें या तो बाहरी स्क्रिप्ट का चयन करना होगा जैसे `<script src =" ... ">` या हमें नियमित रूप से `<script>` टैग के अंदर कोड लिखना होगा।

ऊपर दिए गए उदाहरण को कार्य करने के लिए दो लिपियों में विभाजित किया जा सकता है:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## सारांश

- हम एक पृष्ठ पर जावास्क्रिप्ट कोड जोड़ने के लिए एक `<स्क्रिप्ट>` टैग का उपयोग कर सकते हैं।
- `टाइप` और` भाषा` attribute की आवश्यकता नहीं है।
- एक बाहरी फाइल में लिखी गई स्क्रिप्ट को `<script src ="path/to/script.js"> </script> के साथ डाला जा सकता है।


ब्राउज़र स्क्रिप्ट और वेबपेज के interaction (परस्पर क्रिया) के बारे में जानने के लिए बहुत कुछ है। लेकिन ध्यान रखें कि ट्यूटोरियल का यह हिस्सा जावास्क्रिप्ट भाषा के लिए समर्पित है, इसलिए हमें इसके विशिष्ट ब्राउज़र कार्यान्वयन के साथ खुद को विचलित नहीं करना चाहिए। हम जावास्क्रिप्ट को चलाने के लिए ब्राउज़र का उपयोग करेंगे, जो कई विकल्पों में से ऑनलाइन पढ़ने के लिए बहुत सुविधाजनक है।
