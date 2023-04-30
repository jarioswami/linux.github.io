---
title: Wordpress mysql hacks
date: 2018-07-05 21:24:53
layout: post
tags: [ mysql, sintaxes ]
---
Alguns hacks wordpress que podem ser usados nos sites httd localhost do Linux. 

```
UPDATE wp_postmeta SET meta_value = REPLACE (meta_value, 'texto', '');

UPDATE wp_posts SET post_content = REPLACE (post_content, ' texto', ', texto,');
UPDATE wp_posts SET post_excerpt = REPLACE (post_excerpt, 'Tupinabás', 'Tupinambás');

DELETE FROM wp_posts WHERE post_type = "revision";

UPDATE wp_options SET option_value = replace(option_value, 'http://link', 'http://link') WHERE option_name = 'home' OR option_name = 'siteurl';

UPDATE 	wp_posts SET guid = replace(guid, 'http://link', 'http://link');

UPDATE wp_posts SET post_content = replace(post_content, 'http://link', 'http://link');


UPDATE 'ig_users' SET 'user_pass' = MD5( 'new_password_here' ) WHERE 'ig_users'.'user_login' = "admin_username";

UPDATE wp_posts SET post_type = 'post' WHERE post_type = 'page'


UPDATE wp_users
SET user_pass = MD5('senha')
WHERE user_login = 'login';


UPDATE wp_posts
SET post_author = 'id_novo_autor'
WHERE post_author = 'id_autor_antigo';


//lista de e-mails nos comentarios
SELECT DISTINCT comment_author_email
FROM wp_comments;


DELETE FROM wp_comments
WHERE comment_approved = 'spam';


//tags 0
SELECT * FROM wp_terms wt
INNER JOIN wp_term_taxonomy wtt
ON wt.term_id=wtt.term_id
WHERE wtt.taxonomy='post_tag'
AND wtt.COUNT=0;


Delete specific post meta
DELETE FROM wp_postmeta WHERE meta_key = 'YourMetaKey';

desabilita todos os plugins
UPDATE wp_options SET option_value = '' WHERE option_name = 'active_plugins';

Delete feed cache
DELETE FROM `wp_options` WHERE `option_name` LIKE ('_transient%_feed_%')

Delete all unused post tags
DELETE FROM wp_terms WHERE term_id IN (SELECT term_id FROM wp_term_taxonomy WHERE count = 0 );
DELETE FROM wp_term_taxonomy WHERE term_id not IN (SELECT term_id FROM wp_terms);
DELETE FROM wp_term_relationships WHERE term_taxonomy_id not IN (SELECT term_taxonomy_id FROM wp_term_taxonomy);


UPDATE wp_posts SET post_author=NEW_AUTHOR_ID WHERE post_author=OLD_AUTHOR_ID;


#imagens subdominio .htacess
Redirect 301 /wp-content/uploads http://img.link

```