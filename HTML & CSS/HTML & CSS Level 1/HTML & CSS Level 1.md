الـ HTML هي اختصار لكلمة Hyper Text Markup Language أو لغة ترميز النص الفائق
الفرق بين xhtml و html وhtml5 ان الـ xhtml فيها قواعد وقوانين اكتر والـ HTML5 هي عبارة عن دمج بين الـ HTML والـ JS أو الجافا سكريبت و الـ CSS. 
الـ HTML هي البنية او الاساسات الخاصة بالموقع والـ CSS هي اختصار لـ Cascading Style Sheets وهي مختصة بالالوان والترتيب (يمين، يسار ..) وهكذا والـ Javascript هي مختصة بالجزء الـ Functional أو الوظيفي 	
### معلومات أساسية
Tag وسم
```plaintext
<tag>...</tag>
```
ID معرف خاص
```plaintext
#id
```
Class معرف عام
```plaintext
.class
```
شكل موقع الانترنت الاساسي الـ Basic 
```plaintext
<header> الترويسة
<body> جسم الموقع
<nav> القائمة الرئيسية
<aside> العمود الجانبي
<footer> التذييل
```
في البداية علشان اعمل تصريح الـ html بفتح محرر نص مثل sublime text  او اي محرر نص كودي اخر ونكتب في البداية: 
```plaintext
<!DOCTYPE html>
```
تطبيق: 
```plaintext
<html>
<!-- here start the html file -->
<head>  
</head>
<!-- here is the body of the html file -->
   <body>
     
   </body>

<!-- here is the end of the html file -->
</html>
```
الـ <head> خاص بالجزء اللي بنخاطب فيه السيرفر والـ <body> خاص بالجزء اللي بيظهر على الشاشة 
الجزء
```plaintext
<!-- here start the html file -->
```
هو الجزء الخاص بالـ comment 
بعد كده اول جزء عندي هو الـ meta ودي مش محتاجة نعملها close وبتبقا زي كده 
```plaintext
<head>
	<meta keywords ="Learn, html" />
</head>
```
والـ keywords دي بتقول للسيرفر كلمات مفتاحية عن الويبسايت بتاعنا واللي بتبقا ليها علاقة بالـ SEO اللي هي Search Engine Optimization (حاجة خاصة بمحركات البحث). 
بعد كده عندي حاجة اسمها link ودي بتتكتب زي كده تحت الـ meta
```plaintext
<link rel="stylesheet" href="/css/style.css">
```
والـ href هنا المقصود بيه الـ Hyper Reference اني بقوله انت هاتاخد الـ css من الملف اللي اسمه style.css 
This code is an HTML link element that specifies the location of a CSS file (style.css) for a web page. The "rel" attribute defines the relationship between the linked document and the current HTML document. The "href" attribute specifies the location of the linked document (the CSS file). When the HTML document is loaded in a web browser, it will apply the styles specified in the linked CSS file to the elements on the page.
بعد كده عندي الـ title اللي هو بيبقا اسم الـ tab  في المتصفح وبيتكتب بعد الـ link زي كده: 
```plaintext
<title>Home</title>
```
بعد كده عندي في الـ body حاجة اسمها الـ <div> او القسم  ودي بتكون عبارة عن حاوية لعناصر الـ html زي كده: 
```plaintext
   <body>
     <div>
       Hello world
     </div>
   </body>
```
وده لما افتح الملف الـ html على اي متصفح هاتظهر معايا كلمة hello world 
طيب لو انا عايز اغير لون كلمة hello world  دي للأزرق مثلا: 
هاكتب كده: 
```plaintext
	<body>
     <div style="color:blue">
       Hello world
     </div>
   </body>
```
طيب عايز مثلا اكبر حجم الفونت ، بكتب كده: 
```plaintext
	<body>
     <div style="color:blue; font-size:35px">
       Hello world
     </div>
   </body>
```
طيب انا علشان اخلي ملف الـ HTML بتاعي Clean مش بحط كل حاجة خاصة بنوع الفونت والالوان والكلام ده .. لا بحط الكلام ده في ملف تاني اسمه مثلا style.css اللي هو بيبقا موجود في اللينك زي كده: 
```plaintext
<link rel="stylesheet" href="style.css">
```
وملف style.css ده بيكون في نفس الفولدر بتاع الـ html 
طيب انا بقا عايز اعرف ملف الـ css ده ان الكلمة بتاعة hello world دي بتتكتب بفونت كذا ولون كذا اعملها ازاي؟! 
بستخدم حاجة اسمها الـ id زي كده
```plaintext
<body>
     <div id="website_header" >
       Hello world
     </div>
   </body>
```
وبحاول مخليش مسافات بين الكلام علشان كده بحط _ 
وبروم على ملف الـ css وبكتب كده: 
```plaintext
#website_header {
  color:blue;
  font-size: 35px;
  font-weight: bold;
}
```
طيب لو  عايز اعمل كلام تحتيه زي subtitle كده بعملها ازاي ؟ بستخدم حاجة اسمها class زي كده: 
```plaintext
<body>
     <div id="website_header">
       Hello world
     </div>
     <div class="website_header">
       Hello world
     </div>
   </body>
```
وبروح على ملف الـ css وبعمل كده بالنسبة للـ class 
```plaintext
#website_header {
  color:blue;
  font-size: 35px;
  font-weight: bold;
}

.website_header {
  color:grey;
  font-size:35px;
  font-weight:bold;
}
```
وطبعا في ملف الـ css ممكن اتحكم في الـ <div> اديله اختيارات كتير زي كده: 
```plaintext
#big_wrapper {
	height: 350px;
	width: 500px;
	border: solid 5px #d35400;
	padding: 15px;
	padding-top: 50px;
	margin: 30px;
	margin-left: 200px;
	color: orange;
	font-size: 24px;
	font-family: tahoma;
	font-style: italic;
}
```
الـ Padding هنا المقصود بيه المساحة الخارجية اللي بديها للعنصر 
ممكن اعمل كذا <div> جوه بعض وجواهم بحط كذا id وكذا class 
### الفرق بين الـ ID والـ Class؟ 
ان الـ id بيكون حاجة واحدة بس بيأثر على حاجة واحدة انما الكلاس لما بعملها بتأثر على كذا حاجة يعني لو عملت class وسميته مثلا wrap فكل wrap في ملف الـ HTML هاتاخد نفس التأثيرات اللي على الـ Class 
**طب ما انا ممكن استخدم نفس الـ ID اللي هو  greenColorAll في كذا Dev زي كده:!!**
```plaintext
<div id="lorem_ipsum">
    <p>Lorem ipsum dolor sit amet, <span id="greenColorAll"> consectetur </span> adipiscing elit.</p>
  </div>
  <div id="lorem2">
    <p>sed do eiusmod tempor <span id="greenColorAll">incididunt ut</span>  labore et dolore magna aliqua.</p>
  </div> 
```
**هاقولك صح بالنسبة بالنسبة للـ html لكن ده بيعمل مشاكل في الـ CSS والـ Javascript. 
******IDs should be unique within a page, but using the same ID multiple times is technically valid HTML. However, doing so can cause unexpected behavior when selecting elements with JavaScript or applying styles with CSS, as only the first element with that ID will be selected.
It's generally better to use classes instead of IDs when you want to apply the same style to multiple elements, as classes can be used multiple times without causing issues.
فيه tag اسمه <h1> وده معناه انه الكلام اللي انا بكتبه عايزه يبقا حجمه كبير وممكن اخليه <h2> يبقا اصغر شوية وهكذا وده بحطه جوه الـ <div> زي كده: 
```plaintext
 <div id="main_title">      <h1>Hello World</h1>    </div>    <div id="lorem_ipsum">      <h2>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</h2>    </div>  </body>
```
وفيه tag خاص للـ Paragraph بيبقا اسمه <p></p> 
وفيه tag اسمه span بيبقا كده: <span></span> وده بستخدمه جوه الـ paragraph علشان مثلا ادي كلام معين خصائص تانية وبيكون زي كده: 
```plaintext
<p>Lorem ipsum dolor sit amet, <span class="redColorAll"> consectetur </span> adipiscing elit.</p>
```
طيب علشان اخلي مثلا الكلام اللي واخد تاج h1 يكون centered ومهما اغير في حجم الـwindow بتاعتي يبقا Responsive معايا بروح على ملف الـ css واكتب كده: 
```plaintext
h1 {
  text-align: center;
  width: 100%;
}
```
### علشان ادرج صورة بداخل الـ html بكتب كده: 
### ```plaintext
<img src="" alt="">
```
وفي الـ src بكتب مسار الصورة ويستحسن اني اعمل فولدر للصور اسميه images الفولدر ده يكون جمب ملف الـ html بتاعي. 
وفي خانة الـ alt هنا بكتب كلمة او كلمتين عن الصورة وده اللي بيبان لما الصورة تكون لسه مش بتحمل في المتصفح. 
يعني الشكل النهائي للصورة المفروض يكون حاجة زي كده: 
```plaintext
<img src="images/header.png" alt="header">
```
ممكن اخلي الصورة تكون هي الباجراوند بروح على ملف الـ css وبكتب: 
```plaintext
background-image: url('images/image.png');
```
طيب انا ممكن احدد زي مقاس معين كده الصورة تبقا جواه . بعمل الـ <div> بتاعتي عادي وبروح على ملف الـ css اعمل background color وبحدد الـ height زي ما انا عاوز. 
```plaintext
#nheader {
background-color: purple;
padding: 25px;
height: 150px;
}
```
كده انا عملت الفريم هاحط بقا الصورة زي كده: 
```plaintext
#nheader {
background--image: url: ('image.png');
background-color: purple;
padding: 25px;
height: 150px;
1
```
وممكن كمان احدد انهي جزء من الصورة هو اللي يظهر جوه الـ div بتاعتي زي كده: 
background-position: bottom;
```plaintext
#nheader{
background-image: url(' images/header_pic. jpg');
background-position: bottom;
background-color: purple;
padding: 25px;
height: 150px;
]
```
وممكن احدد الـ anchor point انها تبقا تحت على الشمال مثلا: 
```plaintext
background-position: bottom left;
```
وممكن اخلي الصورة ثابتة متتحركش وانا بعمل scroll عن طريق الامر ده: 
```plaintext
background-attachment: fixed;
```
ملحوظة: ممكن أجمع الـ ٣ سطور بتوع الـ background في سطر واحد بس زي كده: 
```plaintext
background: url(' images/header_pic. jpg') bottom left purple;
```

### طريقة كتابة الـ Comment في الـ CSS 
احنا كنا بنكتب الكومنت كده في الـ html : 
```plaintext
<!-- this is comment -->
```
علشان نكتب كومنت في الـ css بنكتبه كده: 
```plaintext
/* this is comment */
```
وممكن نستخدم الكومنت في اننا نعطل كود معين بدل ما نحذفه كله. 
ملحوظة: أمر img من الأوامر الأساسية معايا يعني مثلا لو حبيت اضيف Border لونه أبيض لكل الصور في ملف الـ html بتاعي بكتب كده في ملف الـ css: 
```plaintext
img {
border: solid 2px white;
}
```
### ازاي أضيف Hyperlink  في ملف الـ HTML ؟ 
بكتب الكود ده: 
```plaintext
<ahref=""></a>
```
وبعدين بحط الـ url بتاعي والكلمة اللي عايزها تبقا hyperlink زي كده: 
```plaintext
<a href="http://www.google.com">Google</a>
```
كده كلمة Google هي اللي هاتظهر ولما اضغط عليها هاتوديني على لينك جوجل
ممكن كمان اشيل الخط اللي تحت كلمة جوجل عن طريق اني بروح على ملف الـ css وبحط الكود ده: 
```plaintext
a {  text-decoration: none;}
```
وممكن اضيف طبعًا هنا لون بس هايحصل مشكلة هي ان اي حاجة انا عاملها Hyperlink كده هاتاخد نفس اللون طب احل الموضوع ده ازاي؟ انا عايز اخلي مثلا كل عنصر معموله hyperlink ياخد من الـ tag اللي فوقيه اللي العنصر ده تابع ليه. 
هاعمل كده عن طريق أمر inherit زي كده: 
```plaintext
a {  text-decoration: none;  color: inherit;}
```
طيب لو انا عايز اخلي لما الماوس يجي على الكلمة الكلمة مثلا يبقا لونها احمر ويكون تحتها خط علشان تبان انها hyperlink اعملها ازاي؟ بروح على الـ css وبكتب كده: 
```plaintext
a:hover {
text-decoration: underline;
color: red;
}
``` 
وممكن اعمل حاجة اسمها style خاص يعني يكون لعنصر واحد بس وده بيكون في ملف الـ html وبكتبه كده: 
```plaintext
<a style="text-decoration: none; color: white;" href="http://www.google.com">Google</a>
```
وممكن بدل كلمة Google احط مكانها صورة يعني احذف كلمة جوجل واضيف كود اضافة الصور  زي كده: 
```plaintext
<a href="http://www.google.com"> <img src="images/image.jpg" alt="google icon"> </a>
```
### مثال على خطأ مع التصليح: 
ايه المشكلة في الكود ده ؟؟! 
```plaintext
<a style="text-align: center; text-decoration: none; color: white;" href="http://www.google.com">Google</a>
```
he text will not be centered within the page if it's the only content within the HTML body. The text-align property only affects the content within a block-level element, and a hyperlink (<a>) tag is an inline-level element by default.
Try wrapping your hyperlink in a block-level element such as a <div> and apply the text-align property to the <div> instead. For example:
```plaintext
<div style="text-align: center;">
  <a style="text-decoration: none; color: white;" href="http://www.google.com">Google</a>
</div>
```
or one line code like this: 
```plaintext
<div style="text-align:center"> <a style="text-align: center; text-decoration: none; color: white;" href="http://www.google.com">Google</a> </div>
```
### **إدراج قائمة menu navigation**
عندي مصطلحين مهمين وهما ul وهي اختصار لكلمة uncategorized list وli اللي هيا اختصار لكلمة list ودول بيجتمعوا مع بعض علشان يدوني الـ menu navigation اللي هي بتبقا فيها الـ home مثلا والـ about والـ contact وكده. 
الـ ul بتتكتب كده: 
```plaintext
<ul></ul>
```
والـ li بتتكتب كده: 
```plaintext
<li></li>
```
مثال: 
```plaintext
<div id="header">      <ul>        <li>Home Page</li>        <li>Products</li>        <li>Categories</li>        <li>Corporate Solutions</li>        <li>Custom Gifts</li>      </ul>    </div>
```
كده هايضيفلي دول بس في شكل list 
طب احنا عايزين نخليهم جمب بعض نعملها ازاي؟ هاروح على ملف الـ css واكتب كده: 
```plaintext
li {  display: inline-block;}
```
كده هايخليهوملي في سطر واحد، طيب عايز بقا اديلهم لون: بكتب كده: 
```plaintext
li {
display: inline-block;
color: white;
}
```
طيب انا عايز اغير مكانهم واجيبهم على اليمين اعملها ازاي؟ بكتب برده في الcss كده: 
```plaintext
ul {  float: right;}
```
طيب هما كده لازقين في بعض انا عايز اخلي مسافة بين كل واحدة والثانية اعملها ازاي؟! هاروح على الـ li في ملف الـ css واديلها padding left أو right زي كده: 
```plaintext
li {  display: inline-block;  color: white;  padding-left: 10px;}
```
ممكن بقا ادي لينك للاقسام بتاعتي 
```plaintext
<li> <a href="http://www.google.com"></a> Home Page</li>
```
ولو عاوز اعوض عن الرابط بحاجة مؤقتة بدل ما احط لينك ممكن احط هاشتاج # زي كده: 
```plaintext
<li> <a href="#home"></a> Home Page</li>
```
ملحوظة: الـ #Home دي ممكن استخدمها في اني لما اضغط مثلا على كلمة home توديني على جزء معين في نفس الصفحة من تحت عن طريق اني بعمل بعمل div في الجزء اللي انا عايزها توديني عليه لما اضغط عليها وبعدين احط id باسم home 
```plaintext
<div id="home"></div>
```
وممكن برده اخليها توديني على صفحة html تانية يعني بدل كلمة #home تبقا home.html زي كده: 
```plaintext
<li> <a href="home.html"> Home Page</a> </li>
```
### تقسيم الـ div والـ sidebar
ممكن اقسم الـ div لقسمين قسم مثلا يكون الـ width بتاعه 70% والقسم الثاني يكون 30% بس لو خليته سبعين وثلاثين مش هايبقوا جمب بعض فالحل اني انزل واحد أو اثنين في المية  في قسم واحد فيبقا مثلا 70% و28% واخلي الـ margin قيمته تبقا 2٪ اللي هما باقيين
### لمسات إضافية للـ CSS
ممكن احط مجموعة أوامر معينة في ملف الـ CSS قبل ما ارو ح اشتغل HTML بحيث تسهل عليا وانا شغال زي كده: 
```plaintext

.left{ 
	float: left;
}
.right {
	float: right;
}
white {
	color: white;
}
.black {
	color: black;
}
```
بحيث لما اروح احط الـ Class في ملف الـ HTML يبقا هو Already متحدد في الـ CSS
وممكن بقا اختصر كمان واجمع كذا Class مع بعض زي كده: 
```plaintext
<h1 class="white right">SOME DUMMY TEXT</h1>
```
يبقا انا جمعت Class الـ white وClass الـ right مع بعض
وممكن مثلا اعمل class زي كده: 
```plaintext
.options {
	color: yellow;
	font-size: 20px;
}
```
وتكون الـ class دي متطبقة في كذا div بس انا مثلا عايز اطبها في div واحدة بس معينة اعملها ازاي؟ بروح على ملف الـ css واكتب قبل الـ class الـ div اللي انا عايزها تتطبق عليها بس زي كده: 
```plaintext
ul li .options {
	color: yellow;
	font-size: 20px;
}
```
يبقا كده الـClass بتاع options ده هايتطبق في الـ div بتاعة الـ ul 
### ملحوظة في نهاية المستوى الأول: 
كل هذا هو الxhtml وليس html5 يعني ده لغاية دلوقتي هو لغة الـ html القديمة أو الـ vanilla html
السطر الوحيد اللي بنستخدمه في الـ html5 هو الافتتاحية: 
```plaintext
<!DOCTYPE html>
```





# 



