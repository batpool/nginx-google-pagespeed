# nginx-google-pagespeed
Nginx Plus google page speed compiled together to provide faster speed.

clone the repo

run rpm -Uvh nginx-*

systemctl restart nginx

add the following config for page speed

# create the following directory

mkdir /var/ngx_pagespeed_cache
chown nginx:nginx /var/ngx_pagespeed_cache

fut the following code in your nginx server block

# enable ngx_pagespeed
pagespeed on;

pagespeed FileCachePath /var/ngx_pagespeed_cache;

# disable CoreFilters
pagespeed RewriteLevel PassThrough;

# enable collapse whitespace filter
pagespeed EnableFilters collapse_whitespace;

# enable JavaScript library offload
pagespeed EnableFilters canonicalize_javascript_libraries;

# combine multiple CSS files into one
pagespeed EnableFilters combine_css;

# combine multiple JavaScript files into one
pagespeed EnableFilters combine_javascript;

# remove tags with default attributes
pagespeed EnableFilters elide_attributes;

# improve resource cacheability
pagespeed EnableFilters extend_cache;

# flatten CSS files by replacing @import with the imported file
pagespeed EnableFilters flatten_css_imports;
pagespeed CssFlattenMaxBytes 5120;

# defer the loading of images which are not visible to the client
pagespeed EnableFilters lazyload_images;

# enable JavaScript minification
pagespeed EnableFilters rewrite_javascript;

# enable image optimization
pagespeed EnableFilters rewrite_images;

# pre-solve DNS lookup
pagespeed EnableFilters insert_dns_prefetch;

# rewrite CSS to load page-rendering CSS rules first.
pagespeed EnableFilters prioritize_critical_css;
