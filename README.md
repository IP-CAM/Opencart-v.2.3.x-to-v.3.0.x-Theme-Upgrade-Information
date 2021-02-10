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

<?php $filter_row++; ?>

<\?php [$](\w*\b)\+\+\; \?\>

{% set $1 = $1 + 1 %}

<hr>

<?php echo $var['key']; ?>

<\?php echo [$](\w*\b)\[\'(\w*\b)\'\]; \?>

{{ $1.$2 }}

<hr>

<?php if ($error_height) { ?>

<\?php if \([$](\w+\b)\) \{ \?\>

{% if $1 %}

<hr>

<?php if (!$shipping) { ?>

<\?php if \(\![$](\w+\b)\) \{ \?\>

{% if not $1 %}

<hr>

<?php if ($voucher['order']) { ?>

<\?php if \([$](\w+\b)\[\'(\w+\b)\'\]\) \{ \?\>

{% if $1.$2 %}

<hr>

<?php if ($sort == 'pd.name') { ?>

<\?php\s+if\s+\([$](\w+\b) == \'(.*\b)\'\)\s+\{\s+\?\>

{% if $1 == '$2' %}

<hr>

<?php if ($custom_field['type'] == 'date') { ?>

<\?php if \([$](\w+\b)\[\'(.*\b)\'\] == \'(.*\b)\'\) \{ \?\>

{% if $1.$2 == '$3' %}

<hr>

<?php if ($attribute_group['attribute_group_id'] == $attribute_group_id) { ?>

<\?php if \([$](\w+\b)\[\'(.*\b)\'\] == [$](.*\b)\) \{ \?\>

{% if $1.$2 == $3 %}

<hr>

<?php if (in_array($marketplace_code, $marketplaces_processing)) { ?>

<\?php if \(in_array\([$](\w+\b), [$](\w+\b)\)\) \{ \?\>

{% if $1 in $2 %}

<hr>

<?php if (in_array($category['category_id'], $selected)) { ?>

<\?php if \(in_array\([$](\w+\b)\[\'(.*\b)\'\], [$](\w+\b)\)\) \{ \?\>

{% if $3 in $1.$2 %}

<hr>

<?php if (isset($error_name[$language['language_id']])) { ?>

<\?php\s+if\s+\(isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\) \{ \?\>

{% if $1[$2.$3] %}

<hr>

<?php echo (isset($account_custom_field[$custom_field['custom_field_id']]) ? $account_custom_field[$custom_field['custom_field_id']] : $custom_field['value']); ?>

<\?php\s+echo\s+\(isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\s+\?\s+[$](.*\b)\[[$](.*\b)\[\'(.*\b)\'\]\] : [$](.*\b)\[\'(.*\b)\'\]\);\s+\?\>

{% if $1[$2.$3] %} {{ $4[$5.$6] }} {% else %} {{ $7.$8 }} {% endif %}

<hr>

<?php echo (isset($account_custom_field[$custom_field['custom_field_id']]) ? $account_custom_field[$custom_field['custom_field_id']] : ''); ?>

<\?php\s+echo\s+\(isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\s+\?\s+[$](.*\b)\[[$](.*\b)\[\'(.*\b)\'\]\] : \'\'\);\s+\?\>

{% if $1[$2.$3] %} {{ $4[$5.$6] }} {% endif %}

<hr>

<?php echo isset($information_description[$language['language_id']]) ? $information_description[$language['language_id']]['description'] : ''; ?>

<\?php\s+echo\s+isset\([$](\w+\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\)\s+\?\s+[$](.*\b)\[[$](.*\b)\[\'(.*\b)\'\]\]\[\'(.*\b)\'\] : \'\';\s+\?\>

{% if $1[$2.$3] %} {{ $4[$5.$6].$7 }} {% endif %}

<hr>

<?php } elseif ($percentage) { ?>

<\?php \} elseif \([$](\w+\b)\) \{ \?\>

{% elseif $1 %}

<hr>

<?php } elseif ($amazon_login_button_size == 'large') { ?>

<\?php \} elseif \([$](\w+\b) == \'(.*\b)\'\) \{ \?\>

{% elseif $1 == '$2' %}

<hr>

<?php } elseif ($percentage < 0) { ?>

<\?php \} elseif \([$](\w+\b) \> 0\) \{ \?\>

{% elseif $1 in < 0 %}

<hr>

<?php foreach ($var1 as $var2) ?>

<\?php foreach \([$](.*\b) as [$](.*\b)\) \{ \?\>

{% for $2 in $1 %}

<hr>

<?php foreach ($custom_field['custom_field_value'] as $custom_field_value) { ?>

<\?php foreach \([$](.*\b)\[\'(.*\b)\'\] as [$](\w+)\) \{ \?\>

{% for $3 in $1.$2 %}

<hr>

<?php foreach ($setting['returns']['paidby'] as $v) { ?>

<\?php foreach \([$](.*\b)\[\'(.*\b)\'\]\[\'(.*\b)\'\] as [$](\w+)\) \{ \?\>

{% for $4 in $1.$2.$3 %}

<hr>

<?php foreach ($marketplaces as $id => $name) { ?>

<\?php foreach \([$](\w+)\s+as\s+[$](\w+)\s+=\>\s+[$](\w+)\)\s+\{ \?\>

{% for $2, $3 in $1 %}

<hr>

<?php foreach ($capture['shipping_info'] as $key => $shipping_info) { ?>

<\?php foreach \([$](.*)\[\'(.*)\'\]\s+as\s+[$](.*)\s+=\>\s+[$](\w+)\)\s+\{ \?\>

{% for $3, $4 in $1.$2 %}

<hr>










<hr>

You will still need to close off the ifs and for statements with the below syntax.

{% endif %}

{% endfor %}


