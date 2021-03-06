---
title: Configuring custom images for the SKU Selector
description: "Learn how to configure the SKU Selector to display a custom image, different than the default one already used by the SKU."
date: "11/11/2019"
tags: ["custom-images", "sku-selector", "image"]
version: "0.x"
git: "https://github.com/vtex-apps/io-documentation/blob/master/docs/en/Recipes/layout/configuring-custom-images-for-the-sku-selector.md"
---

# Configuring custom images for the SKU Selector

## Introduction

By default, the [SKU selector](https://vtex.io/docs/app/vtex.store-components/sku-selector) component uses **miniatures of SKU images** when rendered.

![sku-selector-images](https://user-images.githubusercontent.com/52087100/68624704-30f2d100-04b6-11ea-852b-df2dd140a09c.png)

These images that the component uses are taken from the SKU's previously given information in admin's Catalog.

However, you can configure the SKU selector to display a **custom image**, meaning an image different than the default one used by the SKU. For example:

![sku-selector-image-custom](https://user-images.githubusercontent.com/52087100/68700719-20992f80-0564-11ea-955a-d65c5a5808be.png)

Follow the step-by-step below to see how to apply this configuration in your store.

## Step by step 

1. In the admin's Catalog, access Products and SKUs. 
2. Select the desired SKU and access the Images tab.
3. Upload the desired custom image, by clicking on **Insert**.

![configuring-sku-selector-images](https://user-images.githubusercontent.com/52087100/68624506-bde95a80-04b5-11ea-8d2a-4f30aa44860a.png)

4. Upload the file in the `File` field and set an ID for the recently uploaded file in the `Label` field. Click on **Save** after performing all your changes.
5. In your theme's code `sku-selector` block, add the `thumbnailImage` prop, whose past value should be the same as the label added in the catalog. For example:

```json
"sku-selector":{  
  "props": {  
    "thumbnailImage": ["LabelName"]  
  }  
},
```

After completing step 5, you will be able to check a brand new image for your SKU selector. 

The problem is that **this image is link to the SKU** through the catalog information, and therefore will also be rendered in its original format when users select the SKU in question.

The way out of this scenario is to **hide the custom image** that's linked to the SKU in the `product-images` block.

6. In the `product-images` block you can use the `hiddenImages` prop to activate a sort of image blacklist. This prop's value should be the custom image's label, the same one used in the previous step. For example: 

```json
"product-images": {  
  "props": {  
    "displayThumbnailsArrows": true,  
    "hiddenImages": ["LabelName"]  
  }  
},
```

<div class="alert alert-info">
Remember to replace the value inserted in the brackets with real values, according to your SKU label.
</div>

Consequently, you'll be able to configure a customized image exclusively for your SKU selector component, without it affecting your store's layout or that of the SKU images displayed to users.

<div class="alert alert-warning">
For this configuration to properly work, <strong>all SKU custom images must have the same label value</strong> (which must be the only value given between brackets). Otherwise, even by following the steps above, the SKU selector will continue to render the default images.
</div>
