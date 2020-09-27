---
title: Lessons Learned Building Gatsby Sites
date: "2020-09-06T23:46:37.121Z"
---



<p>I built two simple sites over the past few months in order to learn the basics of Gatsby. The first one (see <a href="https://gatsby-coding.netlify.com/">https://gatsby-coding.netlify.com/</a>) is really just a page, but even so it incorporates GraphQL to load both the menu and the projects.&nbsp; The other is for a therapist client (see <a href="https://www.barbaragelfandlcsw.com/" target="_blank" rel="noreferrer noopener" aria-label="https://www.barbaragelfandlcsw.com/ (opens in a new tab)">https://www.barbaragelfandlcsw.com/</a> ) – I used one of my garden photos for the header.  Note how the image lazy loads with a blur effect and then comes in to sharp view.</p>



<h2>Why Gatsby?</h2>



<p>In short, there are some great reasons to use Gatsby for a website. Gatsby loads fast.&nbsp; One has a nice lazy-loading of images with Gatsby image.&nbsp; A Gatsby site is easy to update by a developer via the code – this makes it easier to maintain.&nbsp; A happy developer means happier clients.  And hosting for small sites is available for <strong>free</strong> via hosts such as Netlify.</p>



<h2>Lower Your Expectations (at first)</h2>



<p>If you are new to Gatsby, leave yourself plenty of time to learn before promising speedy turnaround to a client. Good news: there are lots of ways to set up a Gatsby site.&nbsp; Bad news: it may take a while to learn those different ways and to choose what works for the needs of the site.</p>



<h2>Study the Code</h2>



<p>One key file in your Gatsby set up is <strong>gatsby.config</strong>. One lesson learned: make sure to add your plugins to this file. For example, I wanted to use Styled Components.&nbsp; I have used this plugin before in some of my React apps.  I added the styled components to my component files. Everything worked fine.&nbsp; Or so I thought.  When I finally deployed the site to Netlify, I was confused by a sudden flash when the site loaded – the CSS did not load immediately.&nbsp; It turned out the fix was simple: add `gatsby-plugin-styled-components` to my gatsby-config.&nbsp; However, finding that solution was not so simple.&nbsp; Someone had had a similar problem; he gave me a name to the problem – FOUC (Flicker of Unstyled Content).&nbsp; Knowing that term helped me find the solution via search engine.</p>



<h2>Gatsby is not WordPress nor is it Drupal</h2>



<p>If you are used to working with WordPress themes, you will find you need to create from scratch (or at least find working code) for certain details of your site.&nbsp; For example, I spent time fine-tuning the mobile piece for the Gelfand site – I even use some React save state knowledge.  Gatsby themes came about after I started the sites I built, but it will be a while before there will be a large amount of professional themes from which to choose.&nbsp; Even so, one will probably want to tailor those themes to specific needs. If you are accustomed to the fields, views, taxonomy, or permission capabilities of Drupal, you can 1) take the time to connect your site with a Drupal back end or 2) learn new ways to accomplish what you need to do or 3) use Drupal instead.</p>



<h2>Ways to Create a Custom Twitter Card</h2>



<p>When I first posted the Gelfand therapist site to Twitter, I got a rather boring card.&nbsp; No image appeared.  I found some plugins that made fancy text cards, but what about an image?&nbsp; It turns out I just needed to add the image to a static folder on my site.  Then I fixed my seo.js to load that image for a Twitter card.&nbsp; The Twitter card then worked as planned.  (Note: this could possibly become a post of its own).</p>



<h2>Why Gatsby for This Therapist Site?</h2>



<figure class="wp-block-image"><img loading="lazy" src="https://biz.leoraw.com/wp-content/uploads/2019/09/old-gelfand.jpg" alt="Barbara Gelfand old site" class="wp-image-82" srcset="https://biz.leoraw.com/wp-content/uploads/2019/09/old-gelfand.jpg 600w, https://biz.leoraw.com/wp-content/uploads/2019/09/old-gelfand-300x220.jpg 300w" sizes="(max-width: 600px) 100vw, 600px" width="600" height="439"></figure>



<p>Barbara’s old site was built with straight HTML and CSS.  While there are benefits to old-fashioned straight code, her site was not being shown on search engine results.  It was not responsive, and it was not so easy to read. </p>



<p>The new design is welcoming, with a larger base font and loads quickly (due to Gatsby).  There is less crowding on the home page – but the contact key information can be easily found in both the footer and the contact page. The site uses React Helmet to fine tune the SEO. It is responsive – feel free to view on your mobile phone.</p>



<figure class="wp-block-image"><img loading="lazy" src="https://biz.leoraw.com/wp-content/uploads/2019/09/gelfand-new-1024x750.png" alt="Barbara Gelfand therapist site" class="wp-image-83" srcset="https://biz.leoraw.com/wp-content/uploads/2019/09/gelfand-new-1024x750.png 1024w, https://biz.leoraw.com/wp-content/uploads/2019/09/gelfand-new-300x220.png 300w, https://biz.leoraw.com/wp-content/uploads/2019/09/gelfand-new-768x562.png 768w, https://biz.leoraw.com/wp-content/uploads/2019/09/gelfand-new.png 1128w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" width="1024" height="750"><figcaption><a href="https://www.barbaragelfandlcsw.com/" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">https://www.barbaragelfandlcsw.com/</a></figcaption></figure>



<p></p>



<h2>What is Next?</h2>



<p>I hope you will join me as I learn more of the <strong>Why Gatsby</strong>.&nbsp; How does one explain Gatsby to a client and to other developers considering learning the Gatsby system? I also have plans to explore the variety of CMS (content management system) packages that work with Gatsby. Best way to follow my tech journey is via <a href="https://twitter.com/leoraw" target="_blank" rel="noreferrer noopener" aria-label="leoraw (opens in a new tab)">leoraw</a> on Twitter.</p>

