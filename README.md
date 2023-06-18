<h1 align="center">Hi 👋, I'm Jeevan</h1>
<h3 align="center">A passionate lead engineer from India</h3>

- 🔭 I’m currently working on [Framework](https://github.com/quintype/quintype-node-framework)

- 🌱 I’m currently learning **Flutter, AWS**

- 📝 I regularly write articles on [https://dev.to/jeevankishore](https://dev.to/jeevankishore)

- 💬 Ask me about **Javascript**

- 📫 How to reach me **kishor080@gmail.com**

<p align="left"> <a href="https://github.com/ryo-ma/github-profile-trophy"><img src="https://github-profile-trophy.vercel.app/?username=jeevan-kishore" alt="jeevan-kishore" /></a> </p>

### Blogs posts
<!-- BLOG-POST-LIST:START -->
 - 💫[Real world use cases of object proxies](https://dev.to/jeevankishore/real-world-use-cases-of-object-proxies-3d87) 
 - &lt;h2&gt;
  
  
  Standard definition
&lt;/h2&gt;

&lt;p&gt;The Proxy object enables you to create a proxy for another object, which can intercept and redefine fundamental operations for that object.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--Lt44erbt--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i9pjxwtq2yow8hk39plf.jpeg&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--Lt44erbt--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i9pjxwtq2yow8hk39plf.jpeg&quot; alt=&quot;Thinking&quot; width=&quot;600&quot; height=&quot;600&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;&lt;em&gt;Let&#39;s simplify that a little.&lt;/em&gt;&lt;/p&gt;

&lt;p&gt;&quot;Customise the behaviour of an object, using handlers&quot; -- in a broad sense. &lt;/p&gt;

&lt;h2&gt;
  
  
  Target and Handlers
&lt;/h2&gt;

&lt;p&gt;Target is the object of concern on which Proxy is applied&lt;/p&gt;

&lt;p&gt;Handlers or traps are functions passed as second parameter to &lt;code&gt;Proxy&lt;/code&gt; which are responsible to handle actions &lpar;such as &lt;code&gt;get&lt;/code&gt;, &lt;code&gt;set&lt;/code&gt; etc&rpar; on the target&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;k&quot;&gt;new&lt;/span&gt; &lt;span class=&quot;nb&quot;&gt;Proxy&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;target&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;handler&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Let&#39;s look at some examples which will add weight around what the statement intends to convey.&lt;/p&gt;

&lt;h2&gt;
  
  
  Handle defaults
&lt;/h2&gt;

&lt;p&gt;Consider a script which is to be used to match the winners with prizes they have won and everyone who participated gets a consolation prize. &lt;/p&gt;

&lt;p&gt;A cleaner approach to coding it as opposed to a long list of &lt;code&gt;if-else&lt;/code&gt; statements or switch is to use &lt;code&gt;Proxy&lt;/code&gt;:&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prizeRegistry&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;na&quot;&gt;karen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;First Prize - BMW X5&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
  &lt;span class=&quot;na&quot;&gt;mark&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;Second Prize - Scooty&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
  &lt;span class=&quot;na&quot;&gt;athira&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;Third Prize - Bicycle&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prizeHandler&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;get&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;in&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;?&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;Consolation prize - Chocolate Bar&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prizeList&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;new&lt;/span&gt; &lt;span class=&quot;nb&quot;&gt;Proxy&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prizeRegistry&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prizeHandler&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;

&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prizeList&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;karen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;c1&quot;&gt;// expected output: &quot;First Prize - BMW X5&quot;&lt;/span&gt;

&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prizeList&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;reena&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
&lt;span class=&quot;c1&quot;&gt;// expected output: &quot;Consolation prize - Chocolate Bar&quot;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;h2&gt;
  
  
  Input validations
&lt;/h2&gt;

&lt;p&gt;With user inputs being a cog in the wheel to most of the applications today. Validations are to be placed to keep the data clean, ironically often as a result the code responsible gets messed up with time.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;validator&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;set&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;===&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;weight&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;!&lt;/span&gt;&lt;span class=&quot;nb&quot;&gt;Number&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;isInteger&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;k&quot;&gt;throw&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;new&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;TypeError&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;The weight is not an integer&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;200&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;k&quot;&gt;throw&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;new&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;RangeError&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;The weight seems invalid&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

    &lt;span class=&quot;c1&quot;&gt;// The default behavior to store the value&lt;/span&gt;
    &lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

    &lt;span class=&quot;c1&quot;&gt;// Indicate success&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;true&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;fish&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;new&lt;/span&gt; &lt;span class=&quot;nb&quot;&gt;Proxy&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;{},&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;validator&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;

&lt;span class=&quot;nx&quot;&gt;fish&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;weight&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;100&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;fish&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;weight&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt; 
&lt;span class=&quot;c1&quot;&gt;// expected output: 100&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;fish&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;weight&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;small&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;    &lt;span class=&quot;c1&quot;&gt;// Throws an exception&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;fish&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;weight&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;300&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;        &lt;span class=&quot;c1&quot;&gt;// Throws an exception&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;h2&gt;
  
  
  Finding an array item object by its property
&lt;/h2&gt;



&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;products&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;new&lt;/span&gt; &lt;span class=&quot;nb&quot;&gt;Proxy&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;[&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;Firefox&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;browser&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;},&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;SeaMonkey&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;browser&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;},&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;Thunderbird&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;mailer&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;],&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;get&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
    &lt;span class=&quot;c1&quot;&gt;// The default behavior to return the value; prop is usually an integer&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;in&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;];&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

    &lt;span class=&quot;c1&quot;&gt;// Get the number of products; an alias of products.length&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;===&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;number&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;length&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

    &lt;span class=&quot;kd&quot;&gt;let&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;result&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
    &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{};&lt;/span&gt;

    &lt;span class=&quot;k&quot;&gt;for&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;of&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;obj&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;===&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;nx&quot;&gt;result&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;].&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;push&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;else&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;product&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;];&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

    &lt;span class=&quot;c1&quot;&gt;// Get a product by name&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;result&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;result&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

    &lt;span class=&quot;c1&quot;&gt;// Get products by type&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;in&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;];&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

    &lt;span class=&quot;c1&quot;&gt;// Get product types&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;prop&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;===&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;nb&quot;&gt;Object&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;keys&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

    &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;undefined&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;

&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;products&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;0&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&rpar;;&lt;/span&gt;          &lt;span class=&quot;c1&quot;&gt;// { name: &#39;Firefox&#39;, type: &#39;browser&#39; }&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;products&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;Firefox&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&rpar;;&lt;/span&gt;  &lt;span class=&quot;c1&quot;&gt;// { name: &#39;Firefox&#39;, type: &#39;browser&#39; }&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;products&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;Chrome&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&rpar;;&lt;/span&gt;   &lt;span class=&quot;c1&quot;&gt;// undefined&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;products&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;browser&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;     &lt;span class=&quot;c1&quot;&gt;// [{ name: &#39;Firefox&#39;, type: &#39;browser&#39; }, { name: &#39;SeaMonkey&#39;, type: &#39;browser&#39; }]&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;products&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;types&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;       &lt;span class=&quot;c1&quot;&gt;// [&#39;browser&#39;, &#39;mailer&#39;]&lt;/span&gt;
&lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;products&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;number&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;      &lt;span class=&quot;c1&quot;&gt;// 3&lt;/span&gt;

&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;The above snippet is from &lt;a href=&quot;https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy#finding_an_array_item_object_by_its_property&quot;&gt;mozilla documentation&lt;/a&gt;, showing how an object in an array of objects can be optimally found using proxy&lt;/p&gt;

&lt;p&gt;There are a number of other real-world usecase&lpar;s&rpar; that could leverage the awesomeness of &lt;code&gt;Proxy&lt;/code&gt; to better maintain and help keep the code cleaner. &lt;/p&gt;

&lt;p&gt;P.S These are the few i use day in and out, there are few more such as DOM manupulations, Property forwarding. You can check em out &lt;a href=&quot;https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy#manipulating_dom_nodes&quot;&gt;here&lt;/a&gt;.&lt;/p&gt;

&lt;p&gt;Hope this helps. Cheers 🍻&lt;/p&gt;

 

 - 💯[Customized payment UPI QR code generation](https://dev.to/jeevankishore/upi-qr-code-generation-4k8a) 
 - &lt;h2&gt;
  
  
  Use case
&lt;/h2&gt;

&lt;p&gt;&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--93bWfJ4t--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vfhirumy1q5k3aulaiie.png&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--93bWfJ4t--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vfhirumy1q5k3aulaiie.png&quot; width=&quot;800&quot; height=&quot;657&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;Recently i had been to a party, paid the bill amount and had to split the cheque with several people.&lt;/p&gt;

&lt;p&gt;Communicating on how much.. where to transfer, which app to use and what not.. was a pain!&lt;/p&gt;

&lt;p&gt;-- Instead --&lt;/p&gt;

&lt;p&gt;Show a QR which works on all apps, scan -&amp;gt; get paid -&amp;gt; done&lt;/p&gt;

&lt;h2&gt;
  
  
  Generator
&lt;/h2&gt;

&lt;p&gt;&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--xWiqiCcQ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u5as450cwz7y2sohwwha.gif&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--xWiqiCcQ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u5as450cwz7y2sohwwha.gif&quot; alt=&quot;live demo&quot; width=&quot;600&quot; height=&quot;533&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;Live demo: &lt;a href=&quot;https://upi-qr.vercel.app/&quot;&gt;https://upi-qr.vercel.app/&lt;/a&gt;&lt;br&gt;
Source code: &lt;a href=&quot;https://github.com/Jeevan-Kishore/upi-qr-generator&quot;&gt;https://github.com/Jeevan-Kishore/upi-qr-generator&lt;/a&gt;&lt;/p&gt;

&lt;h2&gt;
  
  
  Architecture
&lt;/h2&gt;

&lt;ul&gt;
&lt;li&gt;Call the API on click of generateQR with the above mentioned format&lt;/li&gt;
&lt;li&gt;Serverless function creates a QR using the details set via a GET call &lt;code&gt;/api/getqr/[name]/[upi]/[amount]&lt;/code&gt;
&lt;/li&gt;
&lt;li&gt;A deelinking URL is constructed, out of which a QR is generated&lt;/li&gt;
&lt;li&gt;API responds back with a &lt;code&gt;.png&lt;/code&gt; - dataURI&lt;/li&gt;
&lt;li&gt;Canvas of 300x300 is constructed to which received dataURI is set as &lt;code&gt;src&lt;/code&gt;
&lt;/li&gt;
&lt;/ul&gt;

&lt;p&gt;QR generation has a variety of usecase&lpar;s&rpar;, this is just one of them we thought to share.&lt;/p&gt;

&lt;p&gt;Cheers 🍺&lt;/p&gt;

 

 - 🔥[Run android emulator on CircleCI](https://dev.to/jeevankishore/run-android-emulator-on-circleci-2n75) 
 - &lt;p&gt;Running an android emulator on a CI such as CircleCI has been a challenge for a lot of people who want to automate their test cases due to the fact that android emulator require hardware acceleration which is unavailable on debian terminals&lt;/p&gt;

&lt;p&gt;We managed to get a headless emulator running on CircleCI with their iOS terminals.&lt;/p&gt;

&lt;p&gt;iOS terminals need to be set up to accommodate the emulators, they have dependencies such as SDK&#39;s, NDK&#39;s, platform tools, &lt;/p&gt;

&lt;p&gt;We would have to do the following: &lt;/p&gt;

&lt;ul&gt;
&lt;li&gt;Configure ANDROID_SDK_ROOT&lt;/li&gt;
&lt;li&gt;Download SDK Tools and unzip&lt;/li&gt;
&lt;li&gt;Create license directory and agree to all licenses&lt;/li&gt;
&lt;li&gt;Set SDKManager path&lt;/li&gt;
&lt;li&gt;Install the following

&lt;ul&gt;
&lt;li&gt;&quot;platform-tools&quot;&lt;/li&gt;
&lt;li&gt;&quot;platforms;android-29&quot;&lt;/li&gt;
&lt;li&gt;&quot;build-tools;29.0.2&quot;&lt;/li&gt;
&lt;li&gt;&quot;ndk-bundle&quot;&lt;/li&gt;
&lt;li&gt;&quot;system-images;android-29;google_apis;x86_64&quot;&lt;/li&gt;
&lt;li&gt;&quot;emulator&quot;&lt;/li&gt;
&lt;/ul&gt;


&lt;/li&gt;
&lt;/ul&gt;

&lt;p&gt;Let&#39;s create a &lt;code&gt;sh&lt;/code&gt; to do that&lt;/p&gt;

&lt;blockquote&gt;
&lt;p&gt;scripts/install-android-tools.sh&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;
&lt;span class=&quot;k&quot;&gt;if&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;[&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;-d&lt;/span&gt; &lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;]&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;then
    &lt;/span&gt;&lt;span class=&quot;nb&quot;&gt;echo&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;Directory &lt;/span&gt;&lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt; already exists so we&#39;re skipping the install. If you&#39;d like to install fresh tools, edit this script to invalidate the CI cache.&quot;&lt;/span&gt;
    &lt;span class=&quot;nb&quot;&gt;exit &lt;/span&gt;0
&lt;span class=&quot;k&quot;&gt;fi

&lt;/span&gt;&lt;span class=&quot;nb&quot;&gt;mkdir&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;-p&lt;/span&gt; &lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;
&lt;span class=&quot;nb&quot;&gt;cd&lt;/span&gt; &lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;
curl https://dl.google.com/android/repository/sdk-tools-darwin-4333796.zip &lt;span class=&quot;nt&quot;&gt;-o&lt;/span&gt; sdk-tools.zip

unzip sdk-tools.zip

&lt;span class=&quot;nb&quot;&gt;mkdir&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;-p&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;/licenses&quot;&lt;/span&gt;

&lt;span class=&quot;nb&quot;&gt;echo&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;24333f8a63b6825ea9c5514f83c2829b004d1fee&quot;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;/licenses/android-sdk-license&quot;&lt;/span&gt;
&lt;span class=&quot;nb&quot;&gt;echo&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;84831b9409646a918e30573bab4c9c91346d8abd&quot;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;/licenses/android-sdk-preview-license&quot;&lt;/span&gt;
&lt;span class=&quot;nb&quot;&gt;echo&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;d975f751698a77b662f1254ddbeed3901e976f5a&quot;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;/licenses/intel-android-extra-license&quot;&lt;/span&gt;

&lt;span class=&quot;nv&quot;&gt;SDKMANAGER&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt;$ANDROID_SDK_ROOT&lt;/span&gt;/tools/bin/sdkmanager

&lt;span class=&quot;nv&quot;&gt;$SDKMANAGER&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;platform-tools&quot;&lt;/span&gt;
&lt;span class=&quot;nv&quot;&gt;$SDKMANAGER&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;platforms;android-29&quot;&lt;/span&gt;
&lt;span class=&quot;nv&quot;&gt;$SDKMANAGER&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;build-tools;29.0.2&quot;&lt;/span&gt;
&lt;span class=&quot;nv&quot;&gt;$SDKMANAGER&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;ndk-bundle&quot;&lt;/span&gt;
&lt;span class=&quot;nv&quot;&gt;$SDKMANAGER&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;system-images;android-29;google_apis;x86_64&quot;&lt;/span&gt;
&lt;span class=&quot;nv&quot;&gt;$SDKMANAGER&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;emulator&quot;&lt;/span&gt;

&lt;span class=&quot;nb&quot;&gt;echo&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;y&quot;&lt;/span&gt; | &lt;span class=&quot;nb&quot;&gt;sudo&lt;/span&gt; &lt;span class=&quot;nv&quot;&gt;$SDKMANAGER&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;--install&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;ndk;20.0.5594570&quot;&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;--sdk_root&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;k&quot;&gt;${&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt;ANDROID_SDK_ROOT&lt;/span&gt;&lt;span class=&quot;k&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Let&#39;s write a command block on circle ci to set path, run scripts and cache&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight yaml&quot;&gt;&lt;code&gt;  &lt;span class=&quot;na&quot;&gt;android-sdk-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;and&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;set&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;android&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;SDK&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;set ANDROID_SDK_ROOT&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export ANDROID_SDK_ROOT=$HOME/android-tools&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;restore_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;android=tools-v1-{{ checksum &quot;scripts/install-android-tools.sh&quot; }}-{{ arch }}&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;install android tools&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;sh scripts/install-android-tools.sh&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/tools/bin:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/tools:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/platform-tools:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/emulator:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;source $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;sdkmanager --list&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;save_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;android=tools-v1-{{ checksum &quot;scripts/install-android-tools.sh&quot; }}-{{ arch }}&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;paths&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
            &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;/Users/distiller/android-tools&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;All that&#39;s left to do now, is to create the emulator and boot it up as a background job&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight yaml&quot;&gt;&lt;code&gt;
  &lt;span class=&quot;na&quot;&gt;create-launch-android-emulator&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;create&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;and&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;launch&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;android&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;emulators&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;create AVD&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;echo &quot;no&quot; | avdmanager --verbose create avd --force --name &quot;Pixel_3a_API_29&quot; --package &quot;system-images;android-29;google_apis;x86_64&quot;&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;start AVD&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;emulator @Pixel_3a_API_29 -no-window -no-audio&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;background&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;no&quot;&gt;true&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;wait for emulator&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;adb wait-for-device shell &#39;while [[ -z $descriptionlpar;getprop dev.bootcomplete&rpar; ]]; do sleep 1; done;&#39;&lt;/span&gt;

&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Your emulator is now up and running on CCI, &lt;a href=&quot;https://github.com/Jeevan-Kishore/e2e-detox/blob/master/.circleci/config.yml&quot;&gt;here&lt;/a&gt; is the link for the complete configuration of CircleCI&lt;/p&gt;

&lt;p&gt;If you have questions, let us know in the comments and we are looking forward for your feedback 🍻&lt;/p&gt;

 

 - 💫[React native end to end testing on CircleCI](https://dev.to/jeevankishore/react-native-end-to-end-testing-on-circleci-2dib) 
 - &lt;h2&gt;
  
  
  Setup Detox
&lt;/h2&gt;

&lt;p&gt;There is an ⚡ &lt;a href=&quot;https://dev.to/jeevankishore/e2e-detox-react-native-161o&quot;&gt;article&lt;/a&gt; dedicated to how to setup detox and it&#39;s know how&#39;s.&lt;/p&gt;




&lt;p&gt;With Detox now being set, we would like it to run when ever there is a push to a branch. Let&#39;s say master.&lt;/p&gt;

&lt;p&gt;For that, all we have to do is hook up our repo to CircleCI and 📝 write some bit of configuration to get it started.&lt;/p&gt;




&lt;h2&gt;
  
  
  CircleCI configuration
&lt;/h2&gt;



&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight yaml&quot;&gt;&lt;code&gt;&lt;span class=&quot;na&quot;&gt;version&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;m&quot;&gt;2.1&lt;/span&gt;

&lt;span class=&quot;na&quot;&gt;commands&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;node-version&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;node&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;version&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;12&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s1&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Project&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Node&#39;&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;set +x&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;source ~/.bashrc&lt;/span&gt;

            &lt;span class=&quot;s&quot;&gt;curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;export NVM_DIR=&quot;$HOME/.nvm&quot;&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;[ -s &quot;$NVM_DIR/nvm.sh&quot; ] &amp;amp;&amp;amp; \. &quot;$NVM_DIR/nvm.sh&quot;  # This loads nvm&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;[ -s &quot;$NVM_DIR/bash_completion&quot; ] &amp;amp;&amp;amp; \. &quot;$NVM_DIR/bash_completion&quot;&lt;/span&gt;


            &lt;span class=&quot;s&quot;&gt;nvm install 12.13.0&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;NODE_DIR=$descriptionlpar;dirname $descriptionlpar;which node&rpar;&rpar;&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &quot;export PATH=$NODE_DIR:\$PATH&quot; &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;npm-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Get&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;JavaScript&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;dependencies&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Executing node version check&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;node -v&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;restore_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Restore npm cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-npm-{{ checksum &quot;./package-lock.json&quot; }}-{{ arch }}&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Installing JavaScript dependencies&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;npm install&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;save_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Save npm cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-npm-{{ checksum &quot;./package-lock.json&quot; }}-{{ arch }}&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;paths&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
            &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;././node_modules&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;bundle-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Get&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;bundle&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;dependencies&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;restore_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Restore Fastlane cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-gems-{{ checksum &quot;Gemfile.lock&quot; }}-{{ arch }}&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Download Fastlane dependencies&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;bundle install --path ./vendor/bundle&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;save_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Save Fastlane cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-gems-{{ checksum &quot;Gemfile.lock&quot; }}-{{ arch }}&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;paths&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
            &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./vendor/bundle&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;pods-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Get&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;cocoapods&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;dependencies&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;restore_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Restore cocoapods specs and pods&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-cocoapods-{{ checksum &quot;./ios/Podfile.lock&quot; }}-{{ arch }}&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Getting cocoapods dependencies&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./ios&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;bundle exec pod install --deployment&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;save_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Save cocoapods specs and pods cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-cocoapods-{{ checksum &quot;./ios/Podfile.lock&quot; }}-{{ arch }}&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;paths&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
            &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./ios/Pods&lt;/span&gt;
            &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;~/.cocoapods&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;gradle-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Get&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Gradle&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;dependencies&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./android&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Chmod permissions&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;sudo chmod +x ./gradlew&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;restore_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Restore Gradle cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-gradle-{{ checksum &quot;./android/build.gradle&quot; }}-{{ checksum  &quot;./android/app/build.gradle&quot; }}-{{ arch }}&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./android&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Download Gradle dependencies&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./gradlew dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;save_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Save Gradle cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;paths&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
            &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;~/.gradle&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;v1-gradle-{{ checksum &quot;./android/build.gradle&quot; }}-{{ checksum  &quot;./android/app/build.gradle&quot; }}-{{ arch }}&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;android-sdk-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;and&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;set&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;android&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;SDK&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;set ANDROID_SDK_ROOT&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export ANDROID_SDK_ROOT=$HOME/android-tools&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;restore_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;android=tools-v1-{{ checksum &quot;scripts/install-android-tools.sh&quot; }}-{{ arch }}&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;install android tools&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;sh scripts/install-android-tools.sh&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/tools/bin:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/tools:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/platform-tools:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;echo &#39;export PATH=$ANDROID_SDK_ROOT/emulator:$PATH&#39;  &amp;gt;&amp;gt; $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;source $BASH_ENV&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;sdkmanager --list&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;save_cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;android=tools-v1-{{ checksum &quot;scripts/install-android-tools.sh&quot; }}-{{ arch }}&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;paths&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
            &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;/Users/distiller/android-tools&lt;/span&gt;


  &lt;span class=&quot;na&quot;&gt;react-native-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;RN&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;dependencies&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;watchman&quot;&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;HOMEBREW_NO_AUTO_UPDATE=1 brew install watchman&lt;/span&gt;


  &lt;span class=&quot;na&quot;&gt;simulator-dependencies&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;iOS&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;simulator&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;dependencies&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Install&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;applesimutils&quot;&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;HOMEBREW_NO_AUTO_UPDATE=1 brew tap wix/brew&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;HOMEBREW_NO_AUTO_UPDATE=1 brew install applesimutils&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;create-launch-android-emulator&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;create&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;and&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;launch&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;android&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;emulators&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;create AVD&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;echo &quot;no&quot; | avdmanager --verbose create avd --force --name &quot;Pixel_3a_API_29&quot; --package &quot;system-images;android-29;google_apis;x86_64&quot;&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;start AVD&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;emulator @Pixel_3a_API_29 -no-window -no-audio&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;background&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;no&quot;&gt;true&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;wait for emulator&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;adb wait-for-device shell &#39;while [[ -z $descriptionlpar;getprop dev.bootcomplete&rpar; ]]; do sleep 1; done;&#39;&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;clear-detox-cache&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;description&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s&quot;&gt;Clears&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;detox&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;framework&lt;/span&gt;&lt;span class=&quot;nv&quot;&gt; &lt;/span&gt;&lt;span class=&quot;s&quot;&gt;cache&quot;&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Clear detox cache&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;pi&quot;&gt;|&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;npx detox clean-framework-cache&lt;/span&gt;
            &lt;span class=&quot;s&quot;&gt;npx detox build-framework-cache&lt;/span&gt;


&lt;span class=&quot;na&quot;&gt;jobs&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;android-test&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;macos&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;na&quot;&gt;xcode&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;11.3.1&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;attach_workspace&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;at&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;checkout&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;node-version&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;bundle-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;npm-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;react-native-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;gradle-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;android-sdk-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;create-launch-android-emulator&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;clear-detox-cache&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Run android detox build&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;npx detox build -c android.emu.release&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Run android detox test&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;npx detox test -c android.emu.release --headless --record-logs all&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;store_artifacts&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;path&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;././artifacts&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;destination&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./jest-logs&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;store_artifacts&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;path&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;././reports&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;destination&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./reports&lt;/span&gt;


  &lt;span class=&quot;na&quot;&gt;ios-test&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;macos&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;na&quot;&gt;xcode&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;11.3.1&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;steps&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;attach_workspace&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;at&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;checkout&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;node-version&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;bundle-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;npm-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;pods-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;react-native-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;simulator-dependencies&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;clear-detox-cache&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Run iOS detox build&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;npx detox build -c ios.sim.release&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;run&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;working_directory&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;.&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;Run iOS detox test&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;command&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;npx detox test -c ios.sim.release --record-logs all &amp;gt; test-summary.txt&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;store_artifacts&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;path&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;././artifacts&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;destination&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./jest-logs&lt;/span&gt;

      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;na&quot;&gt;store_artifacts&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;path&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;././reports&lt;/span&gt;
          &lt;span class=&quot;na&quot;&gt;destination&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;./reports&lt;/span&gt;


&lt;span class=&quot;na&quot;&gt;workflows&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
  &lt;span class=&quot;na&quot;&gt;version&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;m&quot;&gt;2&lt;/span&gt;

  &lt;span class=&quot;na&quot;&gt;run_detox_tests&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;jobs&lt;/span&gt;&lt;span class=&quot;pi&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;android-test&lt;/span&gt;
      &lt;span class=&quot;pi&quot;&gt;-&lt;/span&gt; &lt;span class=&quot;s&quot;&gt;ios-test&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Let&#39;s walk through some commands to get better context on what&#39;s happening:&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - attach_workspace:
          at: .
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Attach the workspace to the current directory&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;   - checkout
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Pull the repo and checkout to the current branch&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - node-version
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Install node package and check for adequate versions&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - bundle-dependencies
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Install and cache gem bundle dependencies such as cocoapods&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - npm-dependencies
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Install and cache  npm depdendencies&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - pods-dependencies
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Install and cache  cocoapods dependencies&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - react-native-dependencies
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Install and cache  RN dependencies&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - simulator-dependencies
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Install simulator dependencies &lpar;android&rpar;&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight plaintext&quot;&gt;&lt;code&gt;      - clear-detox-cache
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;Clear existing cache of detox for every boot&lt;/p&gt;
&lt;/blockquote&gt;

&lt;p&gt;Please visit the &lt;a href=&quot;https://github.com/Jeevan-Kishore/e2e-detox&quot;&gt;repo&lt;/a&gt; for a working demo&lt;/p&gt;

&lt;p&gt;If you have questions, let us know in the comments and we are looking forward for your feedback 🍻&lt;/p&gt;

 

 - 🚀[Memory leak by anonymous functions](https://dev.to/jeevankishore/memory-leak-by-anonymous-functions-77p) 
 - &lt;p&gt;With introduction of fat arrow functions ➕ the implicit bind magic, JS developers found an everlasting 💛 towards them.&lt;/p&gt;

&lt;p&gt;Although they were eye pleasing and a delight, they bought with a variety of concerns if not implemented wisely.&lt;/p&gt;

&lt;p&gt;One such case i found myself having numerous conversations with my peers about; is having anonymous functions to handle the events which developers find easy to use and miss the subtle ugly memory leak they cause.&lt;/p&gt;

&lt;p&gt;&lt;em&gt;P.S This article won&#39;t be dwelling to the 🐘 depths of memory leak identification and resolutions but to emphasis on the fact that taking the easy route in this case will end up hitting the hardest.&lt;/em&gt;&lt;/p&gt;




&lt;h2&gt;
  
  
  ✨ Theory
&lt;/h2&gt;

&lt;p&gt;An anonymous function might not be cleared by GC &lpar;garbage collection&rpar; efficiently during a mark and sweep phase as the references to it cannot be determined hence GC fails to recover back the allocated memory&lt;/p&gt;




&lt;h2&gt;
  
  
  ✨ Lab setup
&lt;/h2&gt;

&lt;ul&gt;
&lt;li&gt;Production react build running on chrome&lt;/li&gt;
&lt;li&gt;Run about 10k state changes on each scenario of with and without anonymous implementation to trigger re-renders&lt;/li&gt;
&lt;/ul&gt;

&lt;p&gt;&lt;em&gt;Preview&lt;/em&gt;&lt;br&gt;
&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--wbVkOSIw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/i/jvqz4zxx06zaff0ybvtv.png&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--wbVkOSIw--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/i/jvqz4zxx06zaff0ybvtv.png&quot; alt=&quot;Alt Text&quot; width=&quot;800&quot; height=&quot;164&quot;&gt;&lt;/a&gt;&lt;/p&gt;


&lt;h2&gt;
  
  
  ✨ Analysis
&lt;/h2&gt;

&lt;p&gt;That being said, let&#39;s jump on to the crux and look at some stats;&lt;/p&gt;

&lt;p&gt;Recording a snapshot of each implementation clearly depicts a memory leak with the anonymous function implementation&lt;/p&gt;

&lt;p&gt;Snapshot &lt;strong&gt;without&lt;/strong&gt; anonymous functions&lt;br&gt;
&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--1TC_LopW--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://i.ibb.co/0F1ZHKf/Screenshot-2020-05-30-at-4-19-43-PM.png&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--1TC_LopW--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://i.ibb.co/0F1ZHKf/Screenshot-2020-05-30-at-4-19-43-PM.png&quot; alt=&quot;Analysis without anonymous functions&quot; width=&quot;800&quot; height=&quot;189&quot;&gt;&lt;/a&gt;&lt;br&gt;
🔸 &lt;em&gt;&lt;a href=&quot;https://i.ibb.co/0F1ZHKf/Screenshot-2020-05-30-at-4-19-43-PM.png&quot;&gt;fig &lpar;i&rpar;&lt;/a&gt;&lt;/em&gt;&lt;/p&gt;

&lt;p&gt;Snapshot &lt;strong&gt;with&lt;/strong&gt; anonymous functions&lt;br&gt;
&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--MpC4AcjB--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://i.ibb.co/zfwdKWW/Screenshot-2020-05-30-at-4-21-17-PM.png&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--MpC4AcjB--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://i.ibb.co/zfwdKWW/Screenshot-2020-05-30-at-4-21-17-PM.png&quot; alt=&quot;Analysis with anonymous functions&quot; width=&quot;800&quot; height=&quot;184&quot;&gt;&lt;/a&gt;&lt;br&gt;
🔸 &lt;em&gt;&lt;a href=&quot;https://i.ibb.co/zfwdKWW/Screenshot-2020-05-30-at-4-21-17-PM.png&quot;&gt;fig &lpar;ii&rpar;&lt;/a&gt;&lt;/em&gt;&lt;/p&gt;

&lt;p&gt;As we compare fig &lpar;i&rpar; with fig &lpar;ii&rpar; it&#39;s clear that the memory allocation has been freed up by GC in fig &lpar;i&rpar; as opposed to that of fig&lpar;ii&rpar;&lt;/p&gt;

&lt;p&gt;The &lt;em&gt;exaggerated&lt;/em&gt; example intends to portrays the memory leak with the approach; which holds true for apps of multiple complexities in the real world&lt;/p&gt;


&lt;h2&gt;
  
  
  ✨ Conclusion =&amp;gt;
&lt;/h2&gt;

&lt;p&gt;Anonymous fat arrow functions within render methods pave way for a memory leak and ipso facto an &lt;em&gt;anti-pattern&lt;/em&gt;&lt;/p&gt;


&lt;h2&gt;
  
  
  ✨ Show me the code
&lt;/h2&gt;


&lt;div class=&quot;ltag-github-readme-tag&quot;&gt;
  &lt;div class=&quot;readme-overview&quot;&gt;
    &lt;h2&gt;
      &lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--A9-wwsHG--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev.to/assets/github-logo-5a155e1f9a670af7944dd5e12375bc76ed542ea80224905ecaf878b9157cdefc.svg&quot; alt=&quot;GitHub logo&quot;&gt;
      &lt;a href=&quot;https://github.com/Jeevan-Kishore&quot;&gt;
        Jeevan-Kishore
      &lt;/a&gt; / &lt;a href=&quot;https://github.com/Jeevan-Kishore/space-complexity&quot;&gt;
        space-complexity
      &lt;/a&gt;
    &lt;/h2&gt;
    &lt;h3&gt;
      A project to demonstrate space complexity over time
    &lt;/h3&gt;
  &lt;/div&gt;
&lt;/div&gt;





&lt;p&gt;If you have questions, let us know in the comments and we are looking forward for your feedback 🍻&lt;/p&gt;

 

 - 🚀[Build pagination with ES6 async generators and iterables](https://dev.to/jeevankishore/build-pagination-with-es6-async-generators-and-iterables-4l4p) 
 - &lt;h2&gt;
  
  
  What the 🐠 is a generator?
&lt;/h2&gt;

&lt;p&gt;Well, according to the definition :&lt;/p&gt;

&lt;blockquote&gt;
&lt;p&gt;Generators are functions which can be exited and later re-entered. Their context &lpar;variable bindings&rpar; will be saved across re-entrances.&lt;/p&gt;
&lt;/blockquote&gt;

&lt;h2&gt;
  
  
  Fancy, what does this bring to the table? 💭
&lt;/h2&gt;

&lt;p&gt;argh, definition again..  💤&lt;/p&gt;

&lt;blockquote&gt;
&lt;p&gt;Generators in JavaScript -- especially when combined with Promises -- are a very powerful tool for asynchronous programming&lt;/p&gt;
&lt;/blockquote&gt;

&lt;h2&gt;
  
  
  A real world scenario?
&lt;/h2&gt;

&lt;p&gt;After all that definition reading, let&#39;s jump into the core of it. :octocat:&lt;/p&gt;

&lt;p&gt;We had an interesting problem on our hands to tackle. It was to enable pagination to one of our mobile app&#39;s on swipe right.&lt;/p&gt;

&lt;h3&gt;
  
  
  So we use generators for it?
&lt;/h3&gt;

&lt;p&gt;There are other possible solutions, generators are just a cleaner solution.&lt;/p&gt;

&lt;h3&gt;
  
  
  How to do it?
&lt;/h3&gt;

&lt;blockquote&gt;
&lt;p&gt;Create a generator&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;asyncGetContent&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;async&lt;/span&gt; &lt;span class=&quot;kd&quot;&gt;function&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;*&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&rpar;{&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;limit&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;10&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;/* content per page */&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;let&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;offset&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;0&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;/* index of item to start from */&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;let&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;totalCount&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;-&lt;/span&gt;&lt;span class=&quot;mi&quot;&gt;1&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;/* -1 signifies failure */&lt;/span&gt;
  &lt;span class=&quot;k&quot;&gt;while&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;offset&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;===&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;0&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;||&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;offset&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;totalCount&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;try&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;response&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;await&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;k&quot;&gt;await&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;fetch&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;lt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;url&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&rpar;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;json&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;offset&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;offset&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;+&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;limit&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;totalCount&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;response&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;total-count&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;];&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;log&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;`offset + totalCount`&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;offset&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;totalCount&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;yield&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;response&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;catch&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;e&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;console&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;warn&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;`exception during fetch`&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;e&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;yield&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;done&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;true&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;value&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;error&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;

&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;That&#39;s a lot to understand, let&#39;s go through each line.&lt;/p&gt;

&lt;p&gt;⛄ we&#39;ve &lt;code&gt;limit&lt;/code&gt; which defines a variable to set the limit on the results of your choice [need not be a constant]&lt;/p&gt;

&lt;p&gt;⛄ prepare a fetch/ axios/ some API call, shoot it with an &lt;code&gt;await&lt;/code&gt; such that we will resolve the resulting promise.&lt;/p&gt;

&lt;p&gt;⛄ &lt;code&gt;yield&lt;/code&gt; the response. The return will be a promise to be consumed by the async caller using &lt;code&gt;.next&lpar;&rpar;&lt;/code&gt;&lpar;we&#39;ll get to that in the next section&rpar;&lt;/p&gt;

&lt;p&gt;⛄ let&#39;s just handle fetch&lt;/p&gt;




&lt;blockquote&gt;
&lt;p&gt;How do i use this?&lt;/p&gt;
&lt;/blockquote&gt;

&lt;p&gt;All that&#39;s left to do is to initiate and call it within an async function as such:&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;contentGen&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;await&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;asyncGetContent&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;/* initate the generator */&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;after initiation, we can call wherever required &lpar;ex: right swipe / click of a button&rpar; to yield the result&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;content&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;await&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;contentGen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;next&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;use &lt;code&gt;content&lt;/code&gt; [the response from the api in this case] as necessary&lt;/p&gt;

&lt;p&gt;If you have questions, let us know in the comments and we are looking forward for your feedback 🍻&lt;/p&gt;

 

 - 💯[End to End Testing with Detox on React-Native](https://dev.to/jeevankishore/e2e-detox-react-native-161o) 
 - &lt;h3&gt;
  
  
  Assumptions
&lt;/h3&gt;

&lt;p&gt;Before we begin, this article assumes RN &lpar;expo or otherwise&rpar; is set up on your terminal and your app is up and running.&lt;/p&gt;

&lt;p&gt;If not please see &lt;a href=&quot;https://reactnative.dev/docs/environment-setup&quot;&gt;how&lt;/a&gt; to do that.&lt;/p&gt;

&lt;p&gt;We will be proceeding with a setup built using React Native CLI. &lt;/p&gt;

&lt;p&gt;Please ensure the builds are working before integration to make it easier later on to debug if need be.&lt;/p&gt;

&lt;p&gt;There might be requirements such as specific ndk versions to be installed&lt;/p&gt;

&lt;p&gt;P.S Either will do.&lt;/p&gt;

&lt;p&gt;Our app is called &lt;code&gt;rndetox&lt;/code&gt; &lpar;it&#39;s weird. I know.&rpar;&lt;/p&gt;

&lt;blockquote&gt;
&lt;p&gt;There have been breaking changes implemented with detox v18, &lt;/p&gt;

&lt;ol&gt;
&lt;li&gt;&lt;a href=&quot;https://github.com/wix/Detox/blob/master/docs/Guide.Migration.md&quot;&gt;Migration&lt;/a&gt;&lt;/li&gt;
&lt;li&gt;The demo source code is updated for the same in &lt;a href=&quot;https://github.com/Jeevan-Kishore/e2e-detox-18&quot;&gt;this repo&lt;/a&gt; &lt;/li&gt;
&lt;/ol&gt;
&lt;/blockquote&gt;

&lt;h3&gt;
  
  
  Why &lt;em&gt;Detox&lt;/em&gt;?
&lt;/h3&gt;

&lt;p&gt;What does detox offer over others? I&#39;ll let their own &lt;a href=&quot;https://github.com/wix/Detox#about&quot;&gt;page&lt;/a&gt; talk about it &lt;/p&gt;




&lt;h3&gt;
  
  
  🔰 Phase 1 - Setting up detox
&lt;/h3&gt;

&lt;p&gt;By this time, your RN app should be up and running on a mac machine. Let&#39;s proceed setting up Detox.&lt;/p&gt;

&lt;h4&gt;
  
  
  Installing packages:
&lt;/h4&gt;

&lt;p&gt;Install the following packages using your &lt;code&gt;terminal&lt;/code&gt;,&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;   xcode-select &lt;span class=&quot;nt&quot;&gt;--install&lt;/span&gt;
   brew update &lt;span class=&quot;o&quot;&gt;&amp;amp;&amp;amp;&lt;/span&gt; brew &lt;span class=&quot;nb&quot;&gt;install &lt;/span&gt;node
   brew tap wix/brew
   brew &lt;span class=&quot;nb&quot;&gt;install &lt;/span&gt;applesimutils
   npm &lt;span class=&quot;nb&quot;&gt;install&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;-g&lt;/span&gt; detox-cli
   npm &lt;span class=&quot;nb&quot;&gt;install &lt;/span&gt;detox &lt;span class=&quot;nt&quot;&gt;--save-dev&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;If jest is not already installed in your project,&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;       npm &lt;span class=&quot;nb&quot;&gt;install &lt;/span&gt;jest &lt;span class=&quot;nt&quot;&gt;--save-dev&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Use this command for detox to generate a jest scaffolding,&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;      detox init &lt;span class=&quot;nt&quot;&gt;-r&lt;/span&gt; jest
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;It will create a bunch of files under &lt;code&gt;e2e&lt;/code&gt; directory with preset configurations.&lt;/p&gt;

&lt;h4&gt;
  
  
  Add detox configuration:
&lt;/h4&gt;

&lt;p&gt;The following configuration needs to be added in &lt;code&gt;package.json&lt;/code&gt; of the project,&lt;/p&gt;

&lt;p&gt;📃 &lt;em&gt;package.json&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;  &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;detox&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
    &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;configurations&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
      &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android.emu.debug&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;binaryPath&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android/app/build/outputs/apk/debug/app-debug.apk&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;cd android &amp;amp;&amp;amp; ./gradlew app:assembleDebug assembleAndroidTest -DtestBuildType=debug &amp;amp;&amp;amp; cd ..&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android.emulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;device&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
          &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;avdName&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;detoxTestEmulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;},&lt;/span&gt;
      &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android.emu.release&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;binaryPath&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android/app/build/outputs/apk/release/app-release.apk&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;cd android &amp;amp;&amp;amp; ./gradlew app:assembleRelease assembleAndroidTest -DtestBuildType=release &amp;amp;&amp;amp; cd ..&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android.emulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;device&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
          &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;avdName&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;detoxTestEmulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;},&lt;/span&gt;
      &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios.sim.release&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;binaryPath&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios/build/Build/Products/Release-iphonesimulator/rndetox&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;export RCT_NO_LAUNCH_PACKAGER=true &amp;amp;&amp;amp; xcodebuild -workspace ios/a.xcworkspace -scheme a -configuration Release -sdk iphonesimulator -derivedDataPath ios/build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios.simulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;device&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
          &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;iPhone 11 Pro&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;},&lt;/span&gt;
      &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios.sim.debug&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;binaryPath&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios/build/Build/Products/Debug-iphonesimulator/rndetox&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;xcodebuild -workspace ios/a.xcworkspace  -scheme a -configuration Debug -sdk iphonesimulator -derivedDataPath ios/build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios.simulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;device&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
          &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;iPhone 11 Pro&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;},&lt;/span&gt;
    &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;test-runner&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;jest&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;h4&gt;
  
  
  What&#39;s happening through the configuration? 😅
&lt;/h4&gt;

&lt;p&gt;Let&#39;s walk through.&lt;/p&gt;

&lt;p&gt;&lt;em&gt;android&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;      &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android.emu.release&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;binaryPath&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android/app/build/outputs/apk/release/app-release.apk&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;cd android &amp;amp;&amp;amp; ./gradlew app:assembleRelease assembleAndroidTest -DtestBuildType=release &amp;amp;&amp;amp; cd ..&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;android.emulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;device&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
          &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;avdName&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;detoxTestEmulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;The android release configuration consists of :&lt;/p&gt;

&lt;ul&gt;
&lt;li&gt;holds path to the built apk to test&lt;/li&gt;
&lt;li&gt;build commands with build type&lt;/li&gt;
&lt;li&gt;type and name of the emulator &lpar;this name should be the same as the emulator which should be created using android studio&rpar;&lt;/li&gt;
&lt;/ul&gt;

&lt;p&gt;Note: On how to create emulators, &lt;a href=&quot;https://developer.android.com/studio/run/managing-avds&quot;&gt;here&lt;/a&gt; is a doc which details it.&lt;/p&gt;




&lt;p&gt;&lt;em&gt;ios&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;       &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios.sim.release&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;binaryPath&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios/build/Build/Products/Release-iphonesimulator/rndetox&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;export RCT_NO_LAUNCH_PACKAGER=true &amp;amp;&amp;amp; xcodebuild -workspace ios/a.xcworkspace -scheme a -configuration Release -sdk iphonesimulator -derivedDataPath ios/build&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;ios.simulator&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;device&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
          &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;type&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;iPhone 11 Pro&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
        &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;The android release configuration consists of :&lt;/p&gt;

&lt;ul&gt;
&lt;li&gt;path to built binary &lpar;&lt;code&gt;rndetox&lt;/code&gt; is the name of our app hence it&#39;s &lt;code&gt;rndetox&lt;/code&gt;, it would be [app_name].app&rpar;&lt;/li&gt;
&lt;li&gt;build commands with scheme and path to workspace as per the name of the app &lpar;ios/[app_name].xcworkspace&rpar;&lt;/li&gt;
&lt;li&gt;type and device the tests are to run on&lt;/li&gt;
&lt;/ul&gt;

&lt;p&gt;With the detox configuration in place, iOS is all set to be worked with. 🎉&lt;/p&gt;

&lt;p&gt;Android on the other hand, well.. &quot; Needs a lot more work. &quot; ⛄&lt;/p&gt;




&lt;h4&gt;
  
  
  Setup detox with android:
&lt;/h4&gt;

&lt;p&gt;📃 &lt;em&gt;android/app/build.gradle&lt;/em&gt;&lt;/p&gt;

&lt;p&gt;Add the following lines to &lt;code&gt;default&lt;/code&gt; section&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight gradle&quot;&gt;&lt;code&gt;       &lt;span class=&quot;n&quot;&gt;testBuildType&lt;/span&gt; &lt;span class=&quot;n&quot;&gt;System&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;na&quot;&gt;getProperty&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;&#39;testBuildType&#39;&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;s1&quot;&gt;&#39;debug&#39;&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&rpar;&lt;/span&gt;  &lt;span class=&quot;c1&quot;&gt;// This will later be used to control the test apk build type for detox&lt;/span&gt;
       &lt;span class=&quot;n&quot;&gt;testInstrumentationRunner&lt;/span&gt; &lt;span class=&quot;s1&quot;&gt;&#39;androidx.test.runner.AndroidJUnitRunner&#39;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Add the following lines to &lt;code&gt;dependencies&lt;/code&gt; section&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight gradle&quot;&gt;&lt;code&gt;       &lt;span class=&quot;n&quot;&gt;androidTestImplementation&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;&#39;com.wix:detox:+&#39;&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;n&quot;&gt;transitive&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;true&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
       &lt;span class=&quot;n&quot;&gt;androidTestImplementation&lt;/span&gt; &lt;span class=&quot;s1&quot;&gt;&#39;junit:junit:4.12&#39;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;📃 &lt;em&gt;android/app/src/androidTest/java/com/rndetox/DetoxTest.java&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight java&quot;&gt;&lt;code&gt;   &lt;span class=&quot;kn&quot;&gt;package&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;com.rndetox&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;/* change to app package name */&lt;/span&gt;

   &lt;span class=&quot;kn&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;com.wix.detox.Detox&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt;

   &lt;span class=&quot;kn&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;org.junit.Rule&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt;
   &lt;span class=&quot;kn&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;org.junit.Test&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt;
   &lt;span class=&quot;kn&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;org.junit.runner.RunWith&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt;

   &lt;span class=&quot;kn&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;androidx.test.ext.junit.runners.AndroidJUnit4&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt;
   &lt;span class=&quot;kn&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;androidx.test.filters.LargeTest&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt;
   &lt;span class=&quot;kn&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nn&quot;&gt;androidx.test.rule.ActivityTestRule&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;;&lt;/span&gt;

   &lt;span class=&quot;nd&quot;&gt;@RunWith&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;AndroidJUnit4&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;na&quot;&gt;class&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&rpar;&lt;/span&gt;
   &lt;span class=&quot;nd&quot;&gt;@LargeTest&lt;/span&gt;
   &lt;span class=&quot;kd&quot;&gt;public&lt;/span&gt; &lt;span class=&quot;kd&quot;&gt;class&lt;/span&gt; &lt;span class=&quot;nc&quot;&gt;DetoxTest&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt;

       &lt;span class=&quot;nd&quot;&gt;@Rule&lt;/span&gt;
       &lt;span class=&quot;kd&quot;&gt;public&lt;/span&gt; &lt;span class=&quot;nc&quot;&gt;ActivityTestRule&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;MainActivity&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt; &lt;span class=&quot;n&quot;&gt;mActivityRule&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;new&lt;/span&gt; &lt;span class=&quot;nc&quot;&gt;ActivityTestRule&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;lt;&amp;gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nc&quot;&gt;MainActivity&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;na&quot;&gt;class&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;false&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;false&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&rpar;;&lt;/span&gt;

       &lt;span class=&quot;nd&quot;&gt;@Test&lt;/span&gt;
       &lt;span class=&quot;kd&quot;&gt;public&lt;/span&gt; &lt;span class=&quot;kt&quot;&gt;void&lt;/span&gt; &lt;span class=&quot;nf&quot;&gt;runDetoxTests&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt;
           &lt;span class=&quot;nc&quot;&gt;Detox&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;na&quot;&gt;runTests&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;n&quot;&gt;mActivityRule&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&rpar;;&lt;/span&gt;
       &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
   &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;The above file should be created as per the hierarchical order &lt;code&gt;android/app/src/androidTest/java/com/[app_name]/DetoxTest.java&lt;/code&gt;&lt;/p&gt;

&lt;p&gt;📃 &lt;em&gt;android/app/src/main/AndroidManifest.xml&lt;/em&gt;&lt;/p&gt;

&lt;p&gt;The snippet should be added to the &lt;code&gt;&amp;lt;application&lt;/code&gt; tag, this is required for detox to perform as expected &lpar;&lt;a href=&quot;https://developer.android.com/guide/topics/manifest/application-element&quot;&gt;what is this?&lt;/a&gt;&rpar;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight xml&quot;&gt;&lt;code&gt;    android:usesCleartextTraffic=&quot;true&quot;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;📃 &lt;em&gt;android/build.gradle&lt;/em&gt;&lt;/p&gt;

&lt;p&gt;Change &lt;code&gt;minSdkVersion&lt;/code&gt; to &lt;code&gt;18&lt;/code&gt; or higher, add &lt;code&gt;kotlinVersion&lt;/code&gt; if it&#39;s not already present under &lt;code&gt;ext&lt;/code&gt;.&lt;/p&gt;

&lt;p&gt;It should look similar to this,&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight gradle&quot;&gt;&lt;code&gt;    &lt;span class=&quot;n&quot;&gt;ext&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt;
        &lt;span class=&quot;n&quot;&gt;buildToolsVersion&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;28.0.3&quot;&lt;/span&gt;
        &lt;span class=&quot;n&quot;&gt;minSdkVersion&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;18&lt;/span&gt;
        &lt;span class=&quot;n&quot;&gt;compileSdkVersion&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;28&lt;/span&gt;
        &lt;span class=&quot;n&quot;&gt;targetSdkVersion&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;28&lt;/span&gt;
        &lt;span class=&quot;n&quot;&gt;kotlinVersion&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;1.3.61&quot;&lt;/span&gt;
    &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Add &lt;code&gt;classpath &quot;org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlinVersion&quot;&lt;/code&gt; under dependencies&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight gradle&quot;&gt;&lt;code&gt;    &lt;span class=&quot;k&quot;&gt;dependencies&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt;
           &lt;span class=&quot;c1&quot;&gt;// ...&lt;/span&gt;
           &lt;span class=&quot;n&quot;&gt;classpath&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlinVersion&quot;&lt;/span&gt;
       &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Add the following &lt;code&gt;maven&lt;/code&gt; snippet under &lt;code&gt;repositories&lt;/code&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight gradle&quot;&gt;&lt;code&gt;   &lt;span class=&quot;k&quot;&gt;allprojects&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt;
       &lt;span class=&quot;k&quot;&gt;repositories&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt;
                &lt;span class=&quot;c1&quot;&gt;// ... statements&lt;/span&gt;
           &lt;span class=&quot;n&quot;&gt;maven&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;{&lt;/span&gt;
               &lt;span class=&quot;c1&quot;&gt;// All of Detox&#39; artifacts are provided via the npm module&lt;/span&gt;
               &lt;span class=&quot;n&quot;&gt;url&lt;/span&gt; &lt;span class=&quot;s2&quot;&gt;&quot;$rootDir/../node_modules/detox/Detox-android&quot;&lt;/span&gt;
           &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
       &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
   &lt;span class=&quot;o&quot;&gt;}&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;With the above steps done, android is all set to go. 🎉&lt;/p&gt;

&lt;p&gt;⚠️ To verify if this are going good, cross check with this &lt;a href=&quot;https://github.com/Jeevan-Kishore/e2e-detox/commit/8eb5b1ef469b7236d880717d9f439b802a6f1ade&quot;&gt;commit&lt;/a&gt; which shows the required file changes. ⚠️&lt;/p&gt;




&lt;h3&gt;
  
  
  🔰 Phase 2 - Write a test
&lt;/h3&gt;

&lt;p&gt;To see if things fall in place, let&#39;s add a test id and assert it.&lt;/p&gt;

&lt;p&gt;📃 &lt;em&gt;App.js&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;     &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Text&lt;/span&gt;  &lt;span class=&quot;nx&quot;&gt;testID&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;desc-text&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;style&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;styles&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;sectionDescription&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;📃 &lt;em&gt;e2e/firstTest.spec.js&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;   &lt;span class=&quot;nx&quot;&gt;describe&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;Example&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
     &lt;span class=&quot;nx&quot;&gt;beforeEach&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;k&quot;&gt;async&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
       &lt;span class=&quot;k&quot;&gt;await&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;device&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;reloadReactNative&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;
     &lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;

     &lt;span class=&quot;nx&quot;&gt;it&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;should have description text on welcome screen&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;async&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
       &lt;span class=&quot;k&quot;&gt;await&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;expect&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;element&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;by&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;id&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;s1&quot;&gt;desc-text&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&#39;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&rpar;&rpar;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;toBeVisible&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;
     &lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;

   &lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;






&lt;h3&gt;
  
  
  🔰 Phase 3 - Build
&lt;/h3&gt;

&lt;h4&gt;
  
  
  Build a release
&lt;/h4&gt;

&lt;p&gt;&lt;em&gt;iOS:&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;    npx detox build &lt;span class=&quot;nt&quot;&gt;-c&lt;/span&gt; ios.sim.release &lt;span class=&quot;nt&quot;&gt;-l&lt;/span&gt; verbose
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;If there are build errors, build on xcode to get details on the same&lt;/p&gt;

&lt;p&gt;&lt;em&gt;Android:&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;    npx detox build &lt;span class=&quot;nt&quot;&gt;-c&lt;/span&gt; android.emu.release &lt;span class=&quot;nt&quot;&gt;-l&lt;/span&gt; verbose
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;h2&gt;
  
  
  If there are build errors, build on android studio to get details on the same
&lt;/h2&gt;

&lt;h3&gt;
  
  
  🔰 Phase 4 - Test
&lt;/h3&gt;

&lt;h4&gt;
  
  
  Test a release
&lt;/h4&gt;

&lt;p&gt;&lt;em&gt;iOS:&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;    npx detox &lt;span class=&quot;nb&quot;&gt;test&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;-c&lt;/span&gt; ios.sim.release &lt;span class=&quot;nt&quot;&gt;-l&lt;/span&gt; verbose
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;&lt;em&gt;Android:&lt;/em&gt;&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight js-code-highlight&quot;&gt;
&lt;pre class=&quot;highlight shell&quot;&gt;&lt;code&gt;    npx detox &lt;span class=&quot;nb&quot;&gt;test&lt;/span&gt; &lt;span class=&quot;nt&quot;&gt;-c&lt;/span&gt; android.emu.release &lt;span class=&quot;nt&quot;&gt;-l&lt;/span&gt; verbose
&lt;/code&gt;&lt;/pre&gt;

&lt;/div&gt;



&lt;p&gt;Your tests should be passing with flying colors 🌈&lt;/p&gt;




&lt;h3&gt;
  
  
  🔰 Phase 5 - Setting up automation
&lt;/h3&gt;

&lt;p&gt;Where is the fun without automating the entire workflow;&lt;/p&gt;

&lt;p&gt;It&#39;s an 🐘 on it&#39;s own, will try to address them individually.&lt;/p&gt;

&lt;ul&gt;
&lt;li&gt;Integration with CircleCI&lt;/li&gt;
&lt;li&gt;Integration with TravisCI&lt;/li&gt;
&lt;/ul&gt;

&lt;p&gt;Check out the github &lt;a href=&quot;https://github.com/Jeevan-Kishore/e2e-detox-18&quot;&gt;repo&lt;/a&gt; for the entire codebase 🔥&lt;/p&gt;

&lt;p&gt;If you have questions, let us know in the comments and we are looking forward for your feedback 🍻&lt;/p&gt;

 

 - 🚀[React navigation v5](https://dev.to/jeevankishore/react-native-navigation-v5-45e0) 
 - &lt;p&gt;With the launch of &lt;a href=&quot;https://www.npmjs.com/package/@react-navigation/native&quot;&gt;react native v5&lt;/a&gt; about 3 months ago backed by neat &lt;a href=&quot;https://reactnavigation.org/docs/getting-started&quot;&gt;documentation&lt;/a&gt; making life easier with hooks usage and native transitions, we decided to revamp our current navigation.&lt;/p&gt;

&lt;h2&gt;
  
  
  Problem:
&lt;/h2&gt;

&lt;p&gt;Build a navigation system for a an app serving to showcase news content such as collections and stories with configurable paywall to facilitate pay per article / premium content across devices&lt;/p&gt;

&lt;h2&gt;
  
  
  Design
&lt;/h2&gt;

&lt;p&gt;&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--DVgXqD1d--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/6znyw870kdwbzesmi2mo.png&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--DVgXqD1d--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/6znyw870kdwbzesmi2mo.png&quot; alt=&quot;Alt Text&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;ul&gt;
&lt;li&gt;Main screen consists of &lt;a href=&quot;https://reactnavigation.org/docs/bottom-tab-navigator&quot;&gt;bottom tab navigation&lt;/a&gt; of about 4 tabs&lt;/li&gt;
&lt;li&gt;Listing screens to showcase categories / sections&lt;/li&gt;
&lt;li&gt;Content screens to display content&lt;/li&gt;
&lt;/ul&gt;

&lt;h2&gt;
  
  
  Architecture:
&lt;/h2&gt;

&lt;p&gt;&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--sd5ChWng--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/x54wr12f2yxmc9mwtb3s.png&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--sd5ChWng--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/x54wr12f2yxmc9mwtb3s.png&quot; alt=&quot;Alt Text&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;blockquote&gt;
&lt;p&gt;App.js&lt;/p&gt;
&lt;/blockquote&gt;

&lt;p&gt;The root of your application needs to be enclosed within a navigation controller, the children of which would be the stack of screens. This will helps us separate concerns b/w auth flows such as login stack and other flows in our case&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;NavigationContainer&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;useLinking&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;@react-navigation/native&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createNativeStackNavigator&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;@react-navigation/native-stack&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;enableScreens&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react-native-screens&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;





&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;nx&quot;&gt;enableScreens&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;
&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;[&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;initialState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;setInitialState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;]&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;useState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;





&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;     &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;NavigationContainer&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;initialState&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;initialState&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;ref&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;ref&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt;
         &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Navigator&lt;/span&gt;
           &lt;span class=&quot;nx&quot;&gt;screenOptions&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{{&lt;/span&gt;
             &lt;span class=&quot;na&quot;&gt;headerShown&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;false&lt;/span&gt;
           &lt;span class=&quot;p&quot;&gt;}}&lt;/span&gt;
           &lt;span class=&quot;nx&quot;&gt;initialRouteName&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;modalStack&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
         &lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt;
           &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;modalStack&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;ModalStack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;           &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;loginStack&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;LoginStack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;         &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;/Stack.Navigator&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;       &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;/NavigationContainer&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;modal-stack.js&lt;/p&gt;
&lt;/blockquote&gt;

&lt;p&gt;The stack is composed of multiple screens which relate in terms of genre in our case.&lt;/p&gt;

&lt;p&gt;&lt;a href=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--v10zqDBs--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/o9xfr5222a6o4w0kso04.png&quot; class=&quot;article-body-image-wrapper&quot;&gt;&lt;img src=&quot;https://res.cloudinary.com/practicaldev/image/fetch/s--v10zqDBs--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/o9xfr5222a6o4w0kso04.png&quot; alt=&quot;Alt Text&quot;&gt;&lt;/a&gt;&lt;/p&gt;

&lt;p&gt;The noticeable aspect is that the stacks are nested, &lt;code&gt;BottomTabStack&lt;/code&gt; is nested within the modal stack and that will be the initial route where our app should land post launch&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;React&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;BottomTabStack&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;../bottom-tab-navigators/bottom-tab-stack&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createNativeStackNavigator&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;@react-navigation/native-stack&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;SCREEN_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;STACK_LIST&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;../../constants/screen-mapping&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

&lt;span class=&quot;cm&quot;&gt;/* Import screen components such as AuthorsScreen, StoryScreen ... */&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createNativeStackNavigator&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;export&lt;/span&gt; &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;ModalStack&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
  &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Navigator&lt;/span&gt;
    &lt;span class=&quot;nx&quot;&gt;screenOptions&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{{&lt;/span&gt;
      &lt;span class=&quot;na&quot;&gt;headerShown&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;false&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}}&lt;/span&gt;
    &lt;span class=&quot;nx&quot;&gt;initialRouteName&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;STACK_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;bottomTabStack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
  &lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt;
    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SCREEN_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;authorScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;AuthorsScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SCREEN_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;storyScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;StoryScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SCREEN_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;bookMarkScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;BookMarkScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;STACK_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;bottomTabStack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;BottomTabStack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;  &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;/Stack.Navigator&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;

&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;bottom-tab-stack.js&lt;br&gt;
&lt;/p&gt;
&lt;/blockquote&gt;

&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;React&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createBottomTabNavigator&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;@react-navigation/bottom-tabs&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

&lt;span class=&quot;cm&quot;&gt;/* Import necessary constants and components.. */&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Tab&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createBottomTabNavigator&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;tabBarStyle&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;na&quot;&gt;activeTintColor&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;blue&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
  &lt;span class=&quot;na&quot;&gt;style&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
    &lt;span class=&quot;na&quot;&gt;paddingTop&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;mi&quot;&gt;5&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;TabIcons&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;icon&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
  &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;iconColor&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;?&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;blue&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;black&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;/* highlight with a diff color if focused */&lt;/span&gt;

  &lt;span class=&quot;k&quot;&gt;switch&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;icon&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;
    &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;home&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;HomeIcon&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;color&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;iconColor&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&amp;gt;&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;;
&lt;/span&gt;    &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;sections&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SectionIcon&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;color&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;iconColor&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&amp;gt;&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;;
&lt;/span&gt;    &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;search&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SearchIcon&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;color&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;iconColor&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&amp;gt;&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;;
&lt;/span&gt;    &lt;span class=&quot;k&quot;&gt;case&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;my-app&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;MyAppIcon&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;color&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;iconColor&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&amp;gt;&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;;
&lt;/span&gt;    &lt;span class=&quot;na&quot;&gt;default&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt;
      &lt;span class=&quot;k&quot;&gt;break&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
  &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
&lt;span class=&quot;p&quot;&gt;};&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;export&lt;/span&gt; &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;BottomTabStack&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
  &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Tab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Navigator&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;tabBarOptions&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;tabBarStyle&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt;
    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Tab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;BOTTOM_TAB&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;bottomHomeTab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;HomeScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;options&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{{&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarIcon&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;TabIcons&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;home&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;title&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;Home&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarTestID&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;test-id-home&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;/* test id&#39;s for use by automation test tools */&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}}&lt;/span&gt;
    &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Tab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;BOTTOM_TAB&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;bottomCategoryTab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;CategoryScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;options&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{{&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarIcon&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;TabIcons&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;sections&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;title&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;Sections&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;cm&quot;&gt;/* Unique identifier to target category tab */&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarTestID&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;test-id-categ&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}}&lt;/span&gt;
    &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Tab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;BOTTOM_TAB&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;bottomSearchTab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SearchScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;options&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{{&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarIcon&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;TabIcons&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;search&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;title&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;Search&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarTestID&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;test-id-search&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}}&lt;/span&gt;
    &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Tab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;BOTTOM_TAB&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;bottomProfileTab&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;ProfileScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
      &lt;span class=&quot;nx&quot;&gt;options&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{{&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarIcon&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;TabIcons&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;focused&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;my-app&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;title&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;My App&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
        &lt;span class=&quot;na&quot;&gt;tabBarTestID&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;test-id-profile&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;
      &lt;span class=&quot;p&quot;&gt;}}&lt;/span&gt;
    &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;  &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;/Tab.Navigator&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;


&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;



&lt;blockquote&gt;
&lt;p&gt;login-stack.js&lt;/p&gt;
&lt;/blockquote&gt;

&lt;p&gt;This stack abstracts the auth-flow.&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;React&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;react&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;
&lt;span class=&quot;k&quot;&gt;import&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createNativeStackNavigator&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;k&quot;&gt;from&lt;/span&gt; &lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;@react-navigation/native-stack&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;;&lt;/span&gt;

&lt;span class=&quot;cm&quot;&gt;/* Import screen components such as Login, SignUp ... */&lt;/span&gt;

&lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;createNativeStackNavigator&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&rpar;;&lt;/span&gt;

&lt;span class=&quot;k&quot;&gt;export&lt;/span&gt; &lt;span class=&quot;kd&quot;&gt;const&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;LoginStack&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&rpar;&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;=&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;
  &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Navigator&lt;/span&gt;
    &lt;span class=&quot;nx&quot;&gt;screenOptions&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{{&lt;/span&gt;
      &lt;span class=&quot;na&quot;&gt;headerShown&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;kc&quot;&gt;false&lt;/span&gt;
    &lt;span class=&quot;p&quot;&gt;}}&lt;/span&gt;
  &lt;span class=&quot;o&quot;&gt;&amp;gt;&lt;/span&gt;
    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SCREEN_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;loginScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Login&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SCREEN_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;registrationScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SignUp&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;    &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Stack&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;Screen&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;SCREEN_LIST&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;forgotPasswordScreen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;nx&quot;&gt;component&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;=&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;ForgotPassword&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt; &lt;span class=&quot;sr&quot;&gt;/&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;  &lt;span class=&quot;o&quot;&gt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;sr&quot;&gt;/Stack.Navigator&lt;/span&gt;&lt;span class=&quot;err&quot;&gt;&amp;gt;
&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&rpar;;&lt;/span&gt;


&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;



&lt;p&gt;With that being set, we can begin surfing 🏄 through the screens&lt;/p&gt;

&lt;p&gt;If we are navigating within a stack:&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;nx&quot;&gt;navigation&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;navigate&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;&amp;lt;&amp;lt;screen_name&amp;gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;lt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;key&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;val&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;



&lt;p&gt;If we do need to navigate across stacks:&lt;br&gt;
&lt;/p&gt;

&lt;div class=&quot;highlight&quot;&gt;&lt;pre class=&quot;highlight javascript&quot;&gt;&lt;code&gt;&lt;span class=&quot;nx&quot;&gt;navigation&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;.&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;navigate&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;&lpar;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;s2&quot;&gt;&amp;lt;&amp;lt;stack_name&amp;gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;dl&quot;&gt;&quot;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;  
                     &lt;span class=&quot;na&quot;&gt;screen&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;screen_name&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;,&lt;/span&gt;
                     &lt;span class=&quot;na&quot;&gt;params&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;{&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;lt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;param_key&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&amp;gt;&lt;/span&gt; &lt;span class=&quot;p&quot;&gt;:&lt;/span&gt; &lt;span class=&quot;o&quot;&gt;&amp;lt;&amp;lt;&lt;/span&gt;&lt;span class=&quot;nx&quot;&gt;param_val&lt;/span&gt;&lt;span class=&quot;o&quot;&gt;&amp;gt;&amp;gt;&lt;/span&gt;&lt;span class=&quot;p&quot;&gt;}&lt;/span&gt;
                   &lt;span class=&quot;p&quot;&gt;}&rpar;;&lt;/span&gt;
&lt;/code&gt;&lt;/pre&gt;&lt;/div&gt;



&lt;p&gt;There are a lot of ground to cover with react-navigation such as &lt;a href=&quot;https://reactnavigation.org/docs/navigation-events/&quot;&gt;events&lt;/a&gt;, &lt;a href=&quot;https://reactnavigation.org/docs/navigation-lifecycle&quot;&gt;lifecycles&lt;/a&gt; and much more .. &lt;/p&gt;

&lt;p&gt;Will be dropping in a github repo link for an example soon 🔥&lt;/p&gt;

&lt;p&gt;If you have questions, let us know in the comments and we are looking forward for your feedback 🍻&lt;/p&gt;

 
<!-- BLOG-POST-LIST:END -->

<p><img align="center" src="https://github-readme-streak-stats.herokuapp.com/?user=jeevan-kishore&" alt="jeevan-kishore" /></p>

<p><img align="left" src="https://github-readme-stats.vercel.app/api/top-langs?username=jeevan-kishore&show_icons=true&locale=en&layout=donut-vertical" alt="jeevan-kishore" /></p>

<p>&nbsp;<img align="center" src="https://github-readme-stats.vercel.app/api?username=jeevan-kishore&show_icons=true&locale=en&include_all_commits=true&hide_rank=true&&theme=radical&show_total_reviews=true" alt="jeevan-kishore" /></p>

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://dev.to/jeevankishore" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/devto.svg" alt="jeevankishore" height="30" width="40" /></a>
<a href="https://linkedin.com/in/jeevan-kishore" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="jeevan-kishore" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>

<p align="left">
  <a href="https://developer.android.com" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/android/android-original-wordmark.svg" alt="android" width="40" height="40" />
  </a>
  <a href="https://babeljs.io/" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/babeljs/babeljs-icon.svg" alt="babel" width="40" height="40" />
  </a>
  <a href="https://getbootstrap.com" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/bootstrap/bootstrap-plain-wordmark.svg" alt="bootstrap" width="40" height="40" />
  </a>
  <a href="https://canvasjs.com" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/Hardik0307/Hardik0307/master/assets/canvasjs-charts.svg" alt="canvasjs" width="40" height="40" />
  </a>
  <a href="https://www.chartjs.org" target="_blank" rel="noreferrer">
    <img src="https://www.chartjs.org/media/logo-title.svg" alt="chartjs" width="40" height="40" />
  </a>
  <a href="https://circleci.com" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/circleci/circleci-icon.svg" alt="circleci" width="40" height="40" />
  </a>
  <a href="https://www.w3schools.com/css/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="css3" width="40" height="40" />
  </a>
  <a href="https://www.cypress.io" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/simple-icons/simple-icons/6e46ec1fc23b60c8fd0d2f2ff46db82e16dbd75f/icons/cypress.svg" alt="cypress" width="40" height="40" />
  </a>
  <a href="https://d3js.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/d3js/d3js-original.svg" alt="d3js" width="40" height="40" />
  </a>
  <a href="https://www.docker.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="40" height="40" />
  </a>
  <a href="https://www.elastic.co" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/elastic/elastic-icon.svg" alt="elasticsearch" width="40" height="40" />
  </a>
  <a href="https://expressjs.com" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original-wordmark.svg" alt="express" width="40" height="40" />
  </a>
  <a href="https://firebase.google.com/" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/firebase/firebase-icon.svg" alt="firebase" width="40" height="40" />
  </a>
  <a href="https://flutter.dev" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg" alt="flutter" width="40" height="40" />
  </a>
  <a href="https://git-scm.com/" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40" />
  </a>
  <a href="https://golang.org" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/go/go-original.svg" alt="go" width="40" height="40" />
  </a>
  <a href="https://grafana.com" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/grafana/grafana-icon.svg" alt="grafana" width="40" height="40" />
  </a>
  <a href="https://graphql.org" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/graphql/graphql-icon.svg" alt="graphql" width="40" height="40" />
  </a>
  <a href="https://gulpjs.com" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/gulp/gulp-plain.svg" alt="gulp" width="40" height="40" />
  </a>
  <a href="https://heroku.com" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/heroku/heroku-icon.svg" alt="heroku" width="40" height="40" />
  </a>
  <a href="https://www.w3.org/html/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40" />
  </a>
  <a href="https://jasmine.github.io/" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/jasmine/jasmine-icon.svg" alt="jasmine" width="40" height="40" />
  </a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40" />
  </a>
  <a href="https://jestjs.io" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/jestjsio/jestjsio-icon.svg" alt="jest" width="40" height="40" />
  </a>
  <a href="https://karma-runner.github.io/latest/index.html" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/karma.svg" alt="karma" width="40" height="40" />
  </a>
  <a href="https://www.elastic.co/kibana" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/elasticco_kibana/elasticco_kibana-icon.svg" alt="kibana" width="40" height="40" />
  </a>
  <a href="https://kubernetes.io" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="40" height="40" />
  </a>
  <a href="https://www.linux.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40" />
  </a>
  <a href="https://mochajs.org" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/mochajs/mochajs-icon.svg" alt="mocha" width="40" height="40" />
  </a>
  <a href="https://www.mongodb.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" alt="mongodb" width="40" height="40" />
  </a>
  <a href="https://nextjs.org/" target="_blank" rel="noreferrer">
    <img src="https://cdn.worldvectorlogo.com/logos/nextjs-2.svg" alt="nextjs" width="40" height="40" />
  </a>
  <a href="https://nodejs.org" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40" />
  </a>
  <a href="https://www.postgresql.org" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" width="40" height="40" />
  </a>
  <a href="https://reactjs.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" width="40" height="40" />
  </a>
  <a href="https://reactnative.dev/" target="_blank" rel="noreferrer">
    <img src="https://reactnative.dev/img/header_logo.svg" alt="reactnative" width="40" height="40" />
  </a>
  <a href="https://realm.io/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/bestofjs/bestofjs-webui/8665e8c267a0215f3159df28b33c365198101df5/public/logos/realm.svg" alt="realm" width="40" height="40" />
  </a>
  <a href="https://redis.io" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/redis/redis-original-wordmark.svg" alt="redis" width="40" height="40" />
  </a>
  <a href="https://redux.js.org" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/redux/redux-original.svg" alt="redux" width="40" height="40" />
  </a>
  <a href="https://sass-lang.com" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/sass/sass-original.svg" alt="sass" width="40" height="40" />
  </a>
  <a href="https://www.sketch.com/" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/sketchapp/sketchapp-icon.svg" alt="sketch" width="40" height="40" />
  </a>
  <a href="https://svelte.dev" target="_blank" rel="noreferrer">
    <img src="https://upload.wikimedia.org/wikipedia/commons/1/1b/Svelte_Logo.svg" alt="svelte" width="40" height="40" />
  </a>
  <a href="https://travis-ci.org" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/travis-ci/travis-ci-icon.svg" alt="travisci" width="40" height="40" />
  </a>
  <a href="https://www.typescriptlang.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" alt="typescript" width="40" height="40" />
  </a>
  <a href="https://webpack.js.org" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/d00d0969292a6569d45b06d3f350f463a0107b0d/icons/webpack/webpack-original-wordmark.svg" alt="webpack" width="40" height="40" />
  </a>
</p>