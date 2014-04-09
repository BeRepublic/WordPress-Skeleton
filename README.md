# WordPress Skeleton

This is a fork of the [original skeleton repo](https://github.com/markjaquith/WordPress-Skeleton) for Wordpress modified by the BeRepublic Tech Team. We have added some plugins and other common features.

## Assumptions

* WordPress as a Git submodule in `/wp/`
* Custom content directory in `/content/` (cleaner, and also because it can't be in `/wp/`)
* The plugins are hosted in `/content/plugins/`
* `wp-config.php` in the root (because it can't be in `/wp/`)
* All writable directories are symlinked to similarly named locations under `/shared/`.

## Questions & Answers

**Q:** Will you accept pull requests?  
**A:** Maybe — if I think the change is useful. I primarily made this for my own use, and thought people might find it useful. If you want to take it in a different direction and make your own customized skeleton, then just maintain your own fork.

**Q:** Why the `/shared/` symlink stuff for uploads?  
**A:** For local development, create `/shared/` (it is ignored by Git), and have the files live there. For production, have your deploy script (Capistrano is my choice) look for symlinks pointing to `/shared/` and repoint them to some outside-the-repo location (like an NFS shared directory or something). This gives you separation between Git-managed code and uploaded files.

**Q:** What version of WordPress does this track?  
**A:** The latest stable release. Send a pull request if I fall behind.

**Q:** What's the deal with `local-config.php`?  
**A:** It is for local development, which might have different MySQL credentials or do things like enable query saving or debug mode. This file is ignored by Git, so it doesn't accidentally get checked in. If the file does not exist (which it shouldn't, in production), then WordPress will used the DB credentials defined in `wp-config.php`.

**Q:** What is `memcached.php`?  
**A:** This is for people using memcached as an object cache backend. It should be something like: `<?php return array( "server01:11211", "server02:11211" ); ?>`. Programattic generation of this file is recommended.

**Q:** Does this support WordPress in multisite mode?  
**A:** It will, starting with WordPress 3.5 (due out in December, 2012). Earlier versions of WordPress don't support Multisite when WordPress is in a subdirectory.

## Plugins

### Advanced Custom Fields

Pin to official repository for Advanced Custom Fields WordPress plugin from https://github.com/elliotcondon/acf.git.

### WP-Stack

A toolkit for creating professional WordPress deployments from https://github.com/markjaquith/WP-Stack.

### Akismet

Checks your comments against the Akismet web service to see if they look like spam or not. Pin to https://github.com/fleishmanhillard/akismet.git

### W3 Total Cache

Easy Web Performance Optimization (WPO) using caching: browser, page, object, database, minify and content delivery network support.
 Pin to https://github.com/fleishmanhillard/w3-total-cache.git

### Wordpress SEO

WordPress SEO is the most complete WordPress SEO plugin that exists today for WordPress.org users. It incorporates everything from a snippet preview and page analysis functionality that helps you optimize your pages content, images titles, meta descriptions and more to XML sitemaps, and loads of optimization options in between. Pin to https://github.com/Yoast/wordpress-seo.git
