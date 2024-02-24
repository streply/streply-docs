---
sidebar_position: 4
---

# Magento

The official Streply SDK for the Magento e-commerce software.

## Install

The first step is to download the `streply/streply-magento` package using the composer:

```bash
composer require streply/streply-magento
```

Enable module and run migration:

```bash
bin/magento module:enable Streply_StreplyMagento
```

Then upgrade setup:

```bash 
bin/magento setup:upgrade
```

- https://github.com/streply/streply-magento
- https://packagist.org/packages/streply/streply-magento

## Configuration

Add default `Streply DSN` key configuration and set module output in `Config > Streply > General`.

Or set necessary settings using CLI:

```bash
bin/magento config:set streply/general/active 1
bin/magento config:set streply/general/dsnurl https://X@api.streply.com/Y
bin/magento cache:flush
```

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::