Nginx-google-pagespeed
===================

Nginx Plus google page speed compiled together to provide faster speed.

clone the repo

*run rpm -Uvh nginx-**

*systemctl restart nginx*

add the following config for page speed

# Create the following directory

mkdir /var/ngx_pagespeed_cache

chown nginx:nginx /var/ngx_pagespeed_cache

# Put the following code in your nginx server block

pagespeed on;

pagespeed FileCachePath /var/ngx_pagespeed_cache;

pagespeed RewriteLevel PassThrough;

pagespeed EnableFilters collapse_whitespace;

pagespeed EnableFilters canonicalize_javascript_libraries;

pagespeed EnableFilters combine_css;

pagespeed EnableFilters combine_javascript;

pagespeed EnableFilters elide_attributes;

pagespeed EnableFilters extend_cache;

pagespeed EnableFilters flatten_css_imports;

pagespeed CssFlattenMaxBytes 5120;

pagespeed EnableFilters lazyload_images;

pagespeed EnableFilters rewrite_javascript;

pagespeed EnableFilters rewrite_images;

pagespeed EnableFilters insert_dns_prefetch;

pagespeed EnableFilters prioritize_critical_css;

