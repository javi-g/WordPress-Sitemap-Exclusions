# WordPress-Sitemap-Exclusions
A simple list of code snippets to customize and exclude specific content types, taxonomies, and users from the default WordPress sitemap.

## Exclude Users from WordPress Sitemap

This snippet removes all user data from the default WordPress sitemap.

```
function usm_exclude_users_from_sitemap($provider, $name) {
    if ('users' === $name) {
        return false;
    }
    return $provider;
}
add_filter('wp_sitemaps_add_provider', 'usm_exclude_users_from_sitemap', 10, 2);
```

## Exclude Custom Post Type from WordPress Sitemap

Use this code to prevent a specific Custom Post Type (like myCustomCPT) from appearing in your WordPress sitemap.

```
function usm_exclude_my_custom_cpt_from_sitemap($post_types) {
    if (isset($post_types['myCustomCPT'])) {
        unset($post_types['myCustomCPT']);
    }
    return $post_types;
}
add_filter('wp_sitemaps_post_types', 'usm_exclude_my_custom_cpt_from_sitemap');
```

## Exclude Custom Taxonomy from WordPress Sitemap

Add this snippet to your functions.php to exclude a specific custom taxonomy (like myCustomTaxonomy) from the WordPress sitemap.

```
function usm_exclude_my_custom_taxonomy_from_sitemap($taxonomies) {
    if (isset($taxonomies['myCustomTaxonomy'])) {
        unset($taxonomies['myCustomTaxonomy']);
    }
    return $taxonomies;
}
add_filter('wp_sitemaps_taxonomies', 'usm_exclude_my_custom_taxonomy_from_sitemap');
