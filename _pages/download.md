---
layout: default2
---

<header class="pagehead">
   <section class="pagetitle">
    <img class="hideonmobile" src="/assets/img/site/tmp12.svg" alt="Tales of Murder, for readers with time to kill!">
  </section> <!-- end div.pagetitle --> 
  
  {% include smallnav.html %}
  
</header>

<article class="downloads">



  <header class="downloads__header">
    <img src="{{ page.image }}" alt="{{ page.title }} by {{ page.author }}" class="download__img">

    <!-- README IF STATEMENT -->
    {% if site.readtime %}
      {% if site.wpm %}
        {% assign readtime = page.wordcount | divided_by:site.wpm %}
      {% else %}
        {% assign readtime = page.wordcount | divided_by:180 %}
      {% endif %}
    {% endif %}

    <div class="download_details">
      <h1 class="downloads__title">{{ page.title }}</h1>
      {% if page.subtitle %}<h3 class="subtitle">{{ page.subtitle }}</h3>{% endif %}

      <h2 class="downloads__author">{% if page.author %}by <span>{{ page.author }}</span>{% else %}<span>{{ page.series }}</span>{% endif %}</h2>

      <p class="metadata">
        <!-- <span class="wordcount">word count: {{ page.wordcount | thousands_separated }}</span> -->
        <span class="etr">read time:
          {% if site.readtime %}
          {% if readtime > 60 %}
          {% assign readtime_hours = readtime | divided_by: 60 %}
          {% assign readtime_minutes = readtime | modulo:60 %}
            {% if readtime_hours > 1 and readtime_hours < 2 %}1 hour
            {% else %}<span class="hour">{{ readtime_hours }}</span> hr
            {% endif %}{% if readtime_minutes < 1 %}{% elsif readtime_minutes > 1 and readtime_minutes < 1.5 %} and 1 minute {% elsif readtime_minutes > 1.5 %} and <span class="time">{{ readtime_minutes }}</span> min{% endif %}
          {% else %}
            {% if readtime < 1 %}Less than 1 minute {% elsif readtime > 1 and readtime < 1.5 %}1 minute {% elsif readtime > 1.5 %}<span class="time">{{ readtime }}</span> min {% endif %}{% endif %}
          {% endif %}
          </span>
        </p>


        {% if page.preprice %}
        <div class="prebuyh">
          <h3>NOT YET RELEASED!</h3>
          <p class="discount"><span>Pre-Buy today &amp; get 50% off!</span></p>
          <p class="note">NOTE: Only sample available now. Complete novel sent by email upon release.</span></p>
        </div>
      {% endif %}

        <div class="addmargin">
          <p>{{ page.description }}</p>

          {% if page.testimonials %}<p class="testimonials">{{ page.testimonials }}</p>{% endif %}
        
        {% if page.preprice %}
          <p class="download__price"><span class="strikethru">${{ page.price }}</span> ${{ page.preprice }} <span class="prebuy-pitch"> PRELAUNCH PRICE!</span></p>
        {% else %}
          <p class="download__price">${{ page.price }}</p>
        {% endif %}
        </div>

        <div class="download__buttons">
          {% if page.buybutton %}
            {{ page.buybutton }}
            {{ page.downloadsamplebutton }}
          {% else if prebuybutton %}
            <div class="prebuy">
              {{ page.prebuybutton }}
              <p class="prebuy-disclaimer">Pre-buy now and download a full sample. Complete novel will be automatically sent when released.</p>
            </div>
            <div class="prebuysample">
              {{ page.downloadsamplebutton }}
              <p class="prebuy-disclaimer">NOTE: Samples are added to your shopping cart with a $0.00 charge. If only samples are in your cart, you will <span class="bold">NOT</span> be required to provide a credit card, only an email address for delivery.</p>
            </div>
          {% else %}
            <div style="border:1px solid #8b0000;">
              <p style="color:#8b0000;padding:1rem 1rem 0 1rem;">NOT YET RELEASED</p>
            </div>
          {% endif %}
          
        </div>
        <br>
        {% if page.buybutton %}
          <p class="smallnote">NOTE: Samples are added to your shopping cart with a $0.00 charge. If you only have samples are in your cart, you will <strong>NOT</strong> be required to provide a credit card; only an email address for delivery.</p>
        {% endif %}

    </div>


  </header> <!-- end header.downloads__header -->

  <article class="downloads">
    {{ content }}
  </article>

  <div class="download__meta" style="margin: 1rem;">
    <h4>Additional Info</h4>
    <ul>
      <li class="download__cfn"><span class="bold">MBIN No: </span>{{ page.casefileNumber }}</li>
      <li class="download__length"><span class="bold">Length: </span>~ {{ page.wordcount | divided_by: 375 }} pages <span class="pagelengthdisclaimer">(depending on ereader font and font size)</span></li>
      <li class="download__opub"><span class="bold">Original Publication: </span><span class="italics">{{ page.opub }}</span> | {{ page.opubdate }} {% if page.opubissue %} | {{ page.opubissue }} {% endif %}</li>
      <li class="download__repub"><span class="bold">Republication Date: </span>
        {% if page.pubdate %}
          {{ page.pubdate | date: "%b %d, %Y"}}
        {% else %}
          Not yet published.
        {% endif %}
      </li>
    </ul>
  </div>

  </div>



</article>
