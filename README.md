#Upgrading themes from 2.3 to 3.0

Below I have created some regular expression code to help with your PHP IDE to mass search and replace basic PHP syntax with Twig syntax.

<hr>

```php
<?php echo $var; ?>
```

```php
<\?php echo [$](\w*\b)[;] \?\>
```

```php
{{ $1 }}
```

<hr>

```php
<?php echo $error_name[$language['language_id']]; ?>
```

```php
<\?php\s+echo\s+[$](\w+)\[[$](.*)\[\'(.*)\'\]\]\; \?\>
```

```php
{{ $1[$2.$3] }}
```

<hr>

```php
<?php $attribute_row = 0; ?>
```

```php
<\?php [$](\w*\b) = 0[;] \?\>
```

```php
{% set $1 = 0 %}
```

<hr>

```php
<?php $filter_row++; ?>
```
```php
<\?php [$](\w*\b)\+\+\; \?\>
```
```php
{% set $1 = $1 + 1 %}
```

<hr>

```php
<?php echo $var['key']; ?>
```
```php
<\?php echo [$](\w*\b)\[\'(\w*\b)\'\]; \?>
```
```php
{{ $1.$2 }}
```

<hr>

```php
<?php if ($error_height) { ?>
```
```php
<\?php if \([$](\w+\b)\) \{ \?\>
```
```php
{% if $1 %}
```

<hr>

```php
<?php if (!$shipping) { ?>
```
```php
<\?php if \(\![$](\w+\b)\) \{ \?\>
```
```php
{% if not $1 %}
```

<hr>

```php
<?php if ($voucher['order']) { ?>
```
```php
<\?php if \([$](\w+\b)\[\'(\w+\b)\'\]\) \{ \?\>
```
```php
{% if $1.$2 %}
```

<hr>

```php
<?php if ($sort == 'pd.name') { ?>
```
```php
<\?php\s+if\s+\([$](\w+\b) == \'(.*\b)\'\)\s+\{\s+\?\>
```
```php
{% if $1 == '$2' %}
```

<hr>

```php
<?php if ($custom_field['type'] == 'date') { ?>
```
```php
<\?php if \([$](\w+\b)\[\'(.*\b)\'\] == \'(.*\b)\'\) \{ \?\>
```
```php
{% if $1.$2 == '$3' %}
```

<hr>

```php
<?php if ($attribute_group['attribute_group_id'] == $attribute_group_id) { ?>
```
```php
<\?php if \([$](\w+\b)\[\'(.*\b)\'\] == [$](.*\b)\) \{ \?\>
```
```php
{% if $1.$2 == $3 %}
```

<hr>

```php
<?php if (in_array($marketplace_code, $marketplaces_processing)) { ?>
```
```php
<\?php if \(in_array\([$](\w+\b), [$](\w+\b)\)\) \{ \?\>
```
```php
{% if $1 in $2 %}
```

<hr>

```php
<?php if (in_array($category['category_id'], $selected)) { ?>
```
```php
<\?php if \(in_array\([$](\w+\b)\[\'(.*\b)\'\], [$](\w+\b)\)\) \{ \?\>
```
```php
{% if $3 in $1.$2 %}
```

<hr>

```php
<?php if (isset($error_name[$language['language_id']])) { ?>
```
```php
<\?php\s+if\s+\(isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\) \{ \?\>
```
```php
{% if $1[$2.$3] %}
```

<hr>

```php
<?php echo (isset($account_custom_field[$custom_field['custom_field_id']]) ? $account_custom_field[$custom_field['custom_field_id']] : $custom_field['value']); ?>
```
```php
<\?php\s+echo\s+\(isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\s+\?\s+[$](.*\b)\[[$](.*\b)\[\'(.*\b)\'\]\] : [$](.*\b)\[\'(.*\b)\'\]\);\s+\?\>
```
```php
{% if $1[$2.$3] %} {{ $4[$5.$6] }} {% else %} {{ $7.$8 }} {% endif %}
```

<hr>

```php
<?php echo (isset($account_custom_field[$custom_field['custom_field_id']]) ? $account_custom_field[$custom_field['custom_field_id']] : ''); ?>
```
```php
<\?php\s+echo\s+\(isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\s+\?\s+[$](.*\b)\[[$](.*\b)\[\'(.*\b)\'\]\] : \'\'\);\s+\?\>
```
```php
{% if $1[$2.$3] %} {{ $4[$5.$6] }} {% endif %}
```

<hr>

```php
<?php echo isset($information_description[$language['language_id']]) ? $information_description[$language['language_id']]['description'] : ''; ?>
```
```php
<\?php\s+echo\s+isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\s+\?\s+[$](.*\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\[\'(.*\b)\'\] : \'\';\s+\?\>
```
```php
{% if $1[$2.$3] %} {{ $4[$5.$6].$7 }} {% endif %}
```

<hr>

```php
<?php } elseif ($percentage) { ?>
```
```php
<\?php \} elseif \([$](\w+\b)\) \{ \?\>
```
```php
{% elseif $1 %}
```

<hr>

```php
<?php } elseif ($amazon_login_button_size == 'large') { ?>
```
```php
<\?php \} elseif \([$](\w+\b) == \'(.*\b)\'\) \{ \?\>
```
```php
{% elseif $1 == '$2' %}
```

<hr>

```php
<?php } elseif ($percentage < 0) { ?>
```
```php
<\?php \} elseif \([$](\w+\b) \> 0\) \{ \?\>
```
```php
{% elseif $1 in < 0 %}
```

<hr>

```php
<?php foreach ($var1 as $var2) ?>
```php
<\?php foreach \([$](.*\b) as [$](.*\b)\) \{ \?\>
```php
{% for $2 in $1 %}

<hr>

```php
<?php foreach ($custom_field['custom_field_value'] as $custom_field_value) { ?>
```php
<\?php foreach \([$](.*\b)\[\'(.*\b)\'\] as [$](\w+)\) \{ \?\>
```php
{% for $3 in $1.$2 %}

<hr>

```php
<?php foreach ($setting['returns']['paidby'] as $v) { ?>
```php
<\?php foreach \([$](.*\b)\[\'(.*\b)\'\]\[\'(.*\b)\'\] as [$](\w+)\) \{ \?\>
```php
{% for $4 in $1.$2.$3 %}

<hr>

```php
<?php foreach ($marketplaces as $id => $name) { ?>
```php
<\?php foreach \([$](\w+)\s+as\s+[$](\w+)\s+=\>\s+[$](\w+)\)\s+\{ \?\>
```php
{% for $2, $3 in $1 %}

<hr>

```php
<?php foreach ($capture['shipping_info'] as $key => $shipping_info) { ?>
```php
<\?php foreach \([$](.*)\[\'(.*)\'\]\s+as\s+[$](.*)\s+=\>\s+[$](\w+)\)\s+\{ \?\>
```php
{% for $3, $4 in $1.$2 %}

<hr>

```php
<\?php \} else \{ \?>
```php
{% else %}

<hr>

```php
<\?php echo \(\$language_id == \$language\[\'language_id\'\]\) \? \' class\=\"active\"\' : \'\' \?>
```php
{% if language_id == language.language_id %} class="active"{% endif %}

<hr>

```php
<\?php echo \(\$language_id == \$language\[\'language_id\'\]\) \? \' active\' \: \'\' \?>
```php
{% if language_id == language.language_id %} active{% endif %}

<hr>

```php
<\?php if \(empty\(\$(.+?)\[\'(.+?)\']\)\) { \?>
```php
{% if $1.$2 %}

<hr>

```php
<\?php echo \$language_flag\[\$language\[\'language_id\'\]\] \?>
```php
{{ language_flag[language.language_id] }}

<hr>

```php
<\?php echo \$language\[\'language_id\'\] \?>
```php
{{ language.language_id }}

<hr>

```php
<\?php echo [$](\w*\b)[;] \?\>
```php
{{ $1 }}

<hr>

```php
<\?php foreach \([$](\w+)\s+as\s+[$](\w+)\s+=\>\s+[$](\w+)\)\s+\{ \?\>
```php
{% for $2, $3 in $1 %}

<hr>

```php
<\?php echo strtolower\(\$(.*?)\); \?>
```php
{{ $1 }}

<hr>

You will still need to close off the ifs and for statements with the below syntax.

{% endif %}

{% endfor %}


