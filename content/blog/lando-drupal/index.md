---
title: Lando + Drupal 8 + Second Database
date: "2020-03-01T22:40:32.169Z"
description: Lando is a free, open-source platform for building local Drupal, WordPress or other PHP sites. Learn how to use Lando for a second database.
---


<p>Some people make success look easy. For me, a new piece can be a struggle. When I succeed, I like to cheer a little. I invite you to applaud along with me.</p>



<p>A while back I was working on a migration.  A migration is when you move parts of one site to a different site. My migration kept trying to migrate to itself instead from old site to new site.  I got quite frustrated!</p>



<p>Fast forward to recently, I had the time and the clearness of head to solve the setup properly.  So for those who came seeking the technical solution, here is how to setup a second database with Lando and Drupal 8.</p>



<p>1. Set up the .lando.yml file first.</p>



<pre class="wp-block-code"><code>name: namesite
recipe: drupal8
config:
  webroot: web
services:
  database:
    portforward: 3307
  db2:
    type: mysql
    portforward: 3308</code></pre>



<p>Your .lando.yml file may not quite look like this, but the essential part is in services – the first one, called database, is the new site. The second one, which is not a full site but just a database exported from your old site, I called db2, but you can call it legacy or whatever suits you.  I also added the portforward so I could more easily access either database using Sequel-Pro.</p>



<p>2. Make backups along the way.  If you use Lando, you probably learned that you can use </p>



<pre class="wp-block-code"><code>lando db-import yoursite.sql</code></pre>



<p>to import a database.   You can also do an export as a backup, which come in quite handy if you want to change your site back to where it was, and clearing cache or re-importing config is not getting you to where you want:</p>



<pre class="wp-block-code"><code>lando db-export bk-date.sql</code></pre>



<p>Move the created bk-date.sql (instead of date, type the approximate date that you did the backup, just as a reminder) outside of your project.  Use it by doing a db-import back into your site if you want to go back to an early stage of the site.</p>



<p>3. When setting up your migration, first set up the new site. Make sure Drupal is already installed before importing the old database to the db2 spot. Once the new site is ready, then you can do the db2 import:</p>



<pre class="wp-block-code"><code>lando db-import --host db2 myoldsite.sql --no-wipe</code></pre>



<p>4. This is how the database section of settings.php of your Drupal 8 site might look, with the two databases in places, the top one being the main Drupal 8 site and the second one being your source:</p>



<pre class="wp-block-code"><code>
$databases['default']['default'] = array (
  'database' =&gt; 'drupal8',
  'username' =&gt; 'drupal8',
  'password' =&gt; 'drupal8',
  'prefix' =&gt; '',
  'host' =&gt; 'database',
  'port' =&gt; '3306',
  'namespace' =&gt; 'Drupal\\Core\\Database\\Driver\\mysql',
  'driver' =&gt; 'mysql',
);

 $databases['db2']['default'] = array(
  'database' =&gt; 'database',
  'username' =&gt; 'mysql',
  'password' =&gt; 'mysql',
  'prefix' =&gt; '',
  'host' =&gt; 'db2',
  'port' =&gt; '3306',
  'namespace' =&gt; 'Drupal\Core\Database\Driver\mysql',
  'driver' =&gt; 'mysql',
);</code></pre>



<p>Hope someone finds this helpful!  Thank you for reading.</p>



<p>Vocabulary:</p>



<p><strong>Lando:</strong> Lando is a free, open-source platform built on Docker for building local Drupal, WordPress or other PHP sites. <a href="https://docs.lando.dev/basics/" target="_blank" rel="noreferrer noopener" aria-label="More on Lando (opens in a new tab)">More on Lando</a>.</p>



<p><strong>Drupal: </strong>Drupal is powerful content management software.  <a rel="noreferrer noopener" aria-label="More on Drupal (opens in a new tab)" href="https://www.drupal.org/about" target="_blank">More on Drupal</a>.</p>
