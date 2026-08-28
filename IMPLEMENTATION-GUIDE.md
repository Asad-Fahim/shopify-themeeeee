# Nasir Book Depot - Exact Implementation Guide

## Overview

This document provides exact code changes needed to implement the design system across all pages. Each section includes specific file modifications, CSS additions, and template updates.

---

## 1. Global Design System Implementation

### 1.1 Add Design System CSS Variables

**File**: `snippets/css-variables.liquid`

**Add to the `:root` section (after line 172):**

```liquid
/* Nasir Book Depot Design System Variables */
--nbd-primary-green: {{ settings.primary_button_background.red }}, {{ settings.primary_button_background.green }}, {{ settings.primary_button_background.blue }};
--nbd-dark-gray: {{ settings.heading_color.red }}, {{ settings.heading_color.green }}, {{ settings.heading_color.blue }};
--nbd-gold-accent: {{ settings.secondary_button_background.red }}, {{ settings.secondary_button_background.green }}, {{ settings.secondary_button_background.blue }};
--nbd-cream-bg: {{ settings.background.red }}, {{ settings.background.green }}, {{ settings.background.blue }};
--nbd-white: {{ settings.secondary_background.red }}, {{ settings.secondary_background.green }}, {{ settings.secondary_background.blue }};
--nbd-success-color: {{ settings.success_color.red }}, {{ settings.success_color.green }}, {{ settings.success_color.blue }};
--nbd-error-color: {{ settings.error_color.red }}, {{ settings.error_color.green }}, {{ settings.error_color.blue }};
--nbd-muted-gray: 78, 89, 100;
--nbd-border-color: {{ border_color.red }}, {{ border_color.green }}, {{ border_color.blue }};

/* Typography Overrides */
--nbd-h1-desktop: 62px;
--nbd-h1-tablet: 48px;
--nbd-h1-mobile: 40px;

--nbd-h2-desktop: 54px;
--nbd-h2-tablet: 44px;
--nbd-h2-mobile: 32px;

--nbd-h3-desktop: 40px;
--nbd-h3-tablet: 32px;
--nbd-h3-mobile: 28px;

--nbd-h4-desktop: 34px;
--nbd-h4-tablet: 30px;
--nbd-h4-mobile: 26px;

--nbd-h5-desktop: 26px;
--nbd-h5-tablet: 24px;
--nbd-h5-mobile: 22px;

--nbd-h6-desktop: 20px;
--nbd-h6-tablet: 18px;
--nbd-h6-mobile: 16px;

/* Spacing System */
--nbd-space-1: 4px;
--nbd-space-2: 8px;
--nbd-space-3: 12px;
--nbd-space-4: 16px;
--nbd-space-5: 24px;
--nbd-space-6: 32px;
--nbd-space-7: 48px;
--nbd-space-8: 64px;
--nbd-space-9: 80px;
--nbd-space-10: 96px;

/* Container System */
--nbd-container-max-width: 1320px;
--nbd-container-gutter-mobile: 20px;
--nbd-container-gutter-tablet: 32px;
--nbd-container-gutter-desktop: 40px;
```

### 1.2 Add Design System CSS Classes

**File**: `assets/theme.css`

**Add at the end of the file:**

```css
/* =========================================================
   NASIR BOOK DEPOT DESIGN SYSTEM
   ========================================================= */

/* Button System */
.nbd-button--primary {
  background-color: rgb(var(--nbd-primary-green));
  color: rgb(var(--nbd-white));
  border: 2px solid rgb(var(--nbd-primary-green));
  border-radius: var(--button-border-radius);
  padding: 14px 32px;
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  transition: all 0.2s ease;
  cursor: pointer;
}

.nbd-button--primary:hover {
  background-color: rgba(var(--nbd-primary-green), 0.9);
  border-color: rgba(var(--nbd-primary-green), 0.9);
}

.nbd-button--primary:focus {
  outline: 2px solid rgb(var(--nbd-gold-accent));
  outline-offset: 2px;
}

.nbd-button--secondary {
  background-color: rgb(var(--nbd-gold-accent));
  color: rgb(var(--nbd-dark-gray));
  border: 2px solid rgb(var(--nbd-gold-accent));
  border-radius: var(--button-border-radius);
  padding: 14px 32px;
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  transition: all 0.2s ease;
  cursor: pointer;
}

.nbd-button--secondary:hover {
  background-color: rgba(var(--nbd-gold-accent), 0.9);
  border-color: rgba(var(--nbd-gold-accent), 0.9);
}

.nbd-button--text {
  background-color: transparent;
  color: rgb(var(--nbd-primary-green));
  border: none;
  border-radius: var(--button-border-radius);
  padding: 8px 16px;
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  transition: all 0.2s ease;
  cursor: pointer;
}

.nbd-button--text:hover {
  color: rgb(var(--nbd-gold-accent));
  text-decoration: underline;
}

/* Card System */
.nbd-card {
  background-color: rgb(var(--nbd-white));
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--block-border-radius);
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  padding: var(--nbd-space-6);
  transition: box-shadow 0.2s ease;
}

.nbd-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

/* Typography System */
.nbd-heading-h1 {
  font-size: var(--nbd-h1-mobile);
  line-height: 1.1;
  font-weight: 700;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-5);
}

@media screen and (min-width: 741px) {
  .nbd-heading-h1 {
    font-size: var(--nbd-h1-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-heading-h1 {
    font-size: var(--nbd-h1-desktop);
  }
}

.nbd-heading-h2 {
  font-size: var(--nbd-h2-mobile);
  line-height: 1.2;
  font-weight: 700;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-4);
}

@media screen and (min-width: 741px) {
  .nbd-heading-h2 {
    font-size: var(--nbd-h2-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-heading-h2 {
    font-size: var(--nbd-h2-desktop);
  }
}

.nbd-heading-h3 {
  font-size: var(--nbd-h3-mobile);
  line-height: 1.3;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-3);
}

@media screen and (min-width: 741px) {
  .nbd-heading-h3 {
    font-size: var(--nbd-h3-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-heading-h3 {
    font-size: var(--nbd-h3-desktop);
  }
}

/* Container System */
.nbd-container {
  max-width: var(--nbd-container-max-width);
  margin: 0 auto;
  padding: 0 var(--nbd-container-gutter-mobile);
}

@media screen and (min-width: 741px) {
  .nbd-container {
    padding: 0 var(--nbd-container-gutter-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-container {
    padding: 0 var(--nbd-container-gutter-desktop);
  }
}

/* Section Spacing */
.nbd-section {
  padding-top: var(--vertical-breather);
  padding-bottom: var(--vertical-breather);
}

.nbd-section--tight {
  padding-top: var(--vertical-breather-tight);
  padding-bottom: var(--vertical-breather-tight);
}
```

---

## 2. Cart Page Redesign

### 2.1 Update Cart Section

**File**: `sections/main-cart.liquid`

**Replace the entire cart content structure (lines 64-150):**

```liquid
{%- if cart.item_count > 0 -%}
  <div class="page-content page-content--fluid">
    <div class="cart nbd-cart">
      <div class="cart__content">
        <div class="nbd-cart-items">
          {%- for line_item in cart.items -%}
            <div class="nbd-cart-item-card">
              <div class="nbd-cart-item__image">
                <a href="{{ line_item.url }}" tabindex="-1" aria-hidden="true">
                  <img class="nbd-cart-item__img" loading="lazy" sizes="(max-width: 740px) 80px, 92px" {% render 'image-attributes', image: line_item.image, sizes: '80,92,160,184,240,276' %}>
                </a>
              </div>

              <div class="nbd-cart-item__details">
                <a href="{{ line_item.url }}" class="nbd-cart-item__title">{{ line_item.product.title }}</a>
                
                {%- if line_item.product.has_only_default_variant == false or line_item.properties.size > 0 -%}
                  <div class="nbd-cart-item__options">
                    {%- for option in line_item.options_with_values -%}
                      <span class="nbd-cart-item__option">{{ option.name }}: {{ option.value }}</span>
                    {%- endfor -%}
                    
                    {%- for property in line_item.properties -%}
                      {%- assign property_first_char = property.first | first -%}
                      {%- if property.last != blank and property_first_char != '_' -%}
                        <span class="nbd-cart-item__option">{{ property.first }}: {{ property.last }}</span>
                      {%- endif -%}
                    {%- endfor -%}
                  </div>
                {%- endif -%}

                {%- if line_item.selling_plan_allocation -%}
                  <div class="nbd-cart-item__selling-plan">{{ line_item.selling_plan_allocation.selling_plan.name }}</div>
                {%- endif -%}

                {%- if line_item.discounts.size > 0 -%}
                  <div class="nbd-cart-item__discounts">
                    {%- for discount in line_item.discounts -%}
                      <span class="nbd-cart-item__discount">{{ discount.title }}</span>
                    {%- endfor -%}
                  </div>
                {%- endif -%}

                <div class="nbd-cart-item__price">{{ line_item.final_price | money }}</div>
              </div>

              <div class="nbd-cart-item__actions">
                <div class="nbd-quantity-selector">
                  <input type="number" name="updates[]" class="nbd-quantity-input" value="{{ line_item.quantity }}" min="0" aria-label="{{ 'cart.general.quantity' | t | escape }}">
                </div>
                
                <a href="{{ line_item.url_to_remove }}" class="nbd-cart-item__remove" data-no-instant>{{ 'cart.general.remove' | t }}</a>
                
                <div class="nbd-cart-item__total">{{ line_item.final_line_price | money }}</div>
              </div>
            </div>
          {%- endfor -%}
        </div>
      </div>

      <div class="cart__recap nbd-cart-summary">
        {%- if section.settings.show_order_note -%}
          <div class="nbd-cart-note">
            <label for="cart-note" class="nbd-cart-note__label">{{ 'cart.general.note' | t }}</label>
            <textarea id="cart-note" name="note" class="nbd-cart-note__textarea">{{ cart.note }}</textarea>
          </div>
        {%- endif -%}

        {%- if cart.cart_level_discount_applications.size > 0 -%}
          <div class="nbd-cart-discounts">
            {%- for discount in cart.cart_level_discount_applications -%}
              <div class="nbd-cart-discount">
                <span class="nbd-cart-discount__icon">{%- render 'icon' with 'discount' -%}</span>
                <span class="nbd-cart-discount__title">{{ discount.title }}</span>
                <span class="nbd-cart-discount__amount">-{{ discount.total_allocated_amount | money }}</span>
              </div>
            {%- endfor -%}
          </div>
        {%- endif -%}

        <div class="nbd-cart-subtotal">
          <span class="nbd-cart-subtotal__label">{{ 'cart.general.subtotal' | t }}</span>
          <span class="nbd-cart-subtotal__amount">{{ cart.total_price | money }}</span>
        </div>

        {%- if section.settings.show_shipping_text -%}
          <div class="nbd-cart-shipping-note">{{ 'cart.general.shipping_at_checkout' | t }}</div>
        {%- endif -%}

        <div class="nbd-cart-taxes">
          {%- if shop.taxes_included or shop.shipping_tax Liability != 'not_required' -%}
            {%- if shop.taxes_included -%}
              <span class="nbd-cart-tax">{{ 'cart.general.taxes_included' | t }}</span>
            {%- endif -%}
            {%- if shop.shipping_tax Liability != 'not_required' -%}
              <span class="nbd-cart-tax">{{ 'cart.general.tax_calculated_at_checkout' | t }}</span>
            {%- endif -%}
          {%- endif -%}
        </div>

        <div class="nbd-cart-checkout">
          <button type="submit" name="checkout" class="nbd-button--primary nbd-button--full">{{ 'cart.general.checkout' | t }}</button>
          
          {%- if section.settings.show_payment_methods -%}
            <div class="nbd-cart-payment-methods">
              {%- for type in shop.enabled_payment_types -%}
                {{ type | payment_type_svg_tag: class: 'nbd-payment-icon' }}
              {%- endfor -%}
            </div>
          {%- endif -%}
        </div>
      </div>
    </div>
  </div>
{%- endif -%}
```

### 2.2 Add Cart-Specific CSS

**File**: `assets/theme.css`

**Add to the end of the file:**

```css
/* =========================================================
   NASIR BOOK DEPOT - CART PAGE
   ========================================================= */

.nbd-cart {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--nbd-space-6);
}

@media screen and (min-width: 1000px) {
  .nbd-cart {
    grid-template-columns: 1fr 380px;
  }
}

.nbd-cart-items {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
}

.nbd-cart-item-card {
  background: rgb(var(--nbd-white));
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--block-border-radius);
  padding: var(--nbd-space-5);
  display: grid;
  grid-template-columns: auto 1fr;
  gap: var(--nbd-space-4);
  align-items: start;
  transition: box-shadow 0.2s ease;
}

.nbd-cart-item-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

@media screen and (min-width: 741px) {
  .nbd-cart-item-card {
    grid-template-columns: auto 1fr auto;
    align-items: center;
  }
}

.nbd-cart-item__image {
  width: 80px;
  height: 80px;
  flex-shrink: 0;
}

@media screen and (min-width: 741px) {
  .nbd-cart-item__image {
    width: 92px;
    height: 92px;
  }
}

.nbd-cart-item__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: var(--block-border-radius-reduced);
}

.nbd-cart-item__details {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-2);
}

.nbd-cart-item__title {
  font-size: 16px;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  text-decoration: none;
  line-height: 1.4;
}

.nbd-cart-item__title:hover {
  color: rgb(var(--nbd-primary-green));
}

.nbd-cart-item__options {
  display: flex;
  flex-wrap: wrap;
  gap: var(--nbd-space-2);
}

.nbd-cart-item__option {
  font-size: 13px;
  color: rgb(var(--nbd-muted-gray));
}

.nbd-cart-item__selling-plan {
  font-size: 13px;
  color: rgb(var(--nbd-muted-gray));
}

.nbd-cart-item__discounts {
  display: flex;
  flex-wrap: wrap;
  gap: var(--nbd-space-2);
}

.nbd-cart-item__discount {
  font-size: 12px;
  color: rgb(var(--nbd-success-color));
  background: rgba(var(--nbd-success-color), 0.1);
  padding: 2px 8px;
  border-radius: 2px;
}

.nbd-cart-item__price {
  font-size: 16px;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-cart-item__actions {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-3);
  align-items: flex-end;
}

@media screen and (min-width: 741px) {
  .nbd-cart-item__actions {
    flex-direction: row;
    align-items: center;
    gap: var(--nbd-space-4);
  }
}

.nbd-quantity-selector {
  display: flex;
  align-items: center;
}

.nbd-quantity-input {
  width: 60px;
  height: 40px;
  padding: 0 8px;
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--button-border-radius);
  font-size: 14px;
  text-align: center;
}

.nbd-cart-item__remove {
  font-size: 13px;
  color: rgb(var(--nbd-muted-gray));
  text-decoration: underline;
  cursor: pointer;
}

.nbd-cart-item__remove:hover {
  color: rgb(var(--nbd-error-color));
}

.nbd-cart-item__total {
  font-size: 16px;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-cart-summary {
  background: rgb(var(--secondary-background));
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--block-border-radius);
  padding: var(--nbd-space-6);
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
  position: sticky;
  top: 20px;
}

.nbd-cart-note {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-2);
}

.nbd-cart-note__label {
  font-size: 14px;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-cart-note__textarea {
  width: 100%;
  min-height: 80px;
  padding: var(--nbd-space-3);
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--button-border-radius);
  font-size: 14px;
  font-family: inherit;
  resize: vertical;
}

.nbd-cart-discounts {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-2);
}

.nbd-cart-discount {
  display: flex;
  align-items: center;
  gap: var(--nbd-space-2);
  font-size: 13px;
  color: rgb(var(--nbd-success-color));
}

.nbd-cart-discount__icon {
  width: 16px;
  height: 16px;
}

.nbd-cart-subtotal {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: var(--nbd-space-4);
  border-top: 1px solid rgb(var(--nbd-border-color));
}

.nbd-cart-subtotal__label {
  font-size: 16px;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-cart-subtotal__amount {
  font-size: 18px;
  font-weight: 700;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-cart-shipping-note {
  font-size: 13px;
  color: rgb(var(--nbd-muted-gray));
  text-align: center;
}

.nbd-cart-taxes {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-1);
}

.nbd-cart-tax {
  font-size: 12px;
  color: rgb(var(--nbd-muted-gray));
  text-align: center;
}

.nbd-cart-checkout {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
}

.nbd-button--full {
  width: 100%;
}

.nbd-cart-payment-methods {
  display: flex;
  justify-content: center;
  gap: var(--nbd-space-3);
  flex-wrap: wrap;
}

.nbd-payment-icon {
  width: 32px;
  height: 20px;
}
```

---

## 3. Customer Account Pages Redesign

### 3.1 Update Account Section

**File**: `sections/main-customers-account.liquid`

**Replace the account content structure (lines 54-130):**

```liquid
<div class="account account--order-list">
  <div class="container container--small nbd-account-container">
    {%- if customer.orders.size == 0 -%}
      <div class="page-header page-header--small {% if section.blocks.size == 1 %}page-header--alone{% endif %}">
        <div class="page-header__text-wrapper text-container">
          <h1 class="nbd-heading-h1">{{ 'customer.orders.title' | t }} <span class="bubble-count bubble-count--top">{{ customer.orders.size }}</span></h1>
          <p class="nbd-account-empty-text">{{ 'customer.orders.no_orders' | t }}</p>

          <div class="button-wrapper">
            <a href="{{ routes.all_products_collection_url }}" class="nbd-button--primary">{{ 'customer.orders.start_shopping' | t }}</a>
          </div>
        </div>
      </div>

      <div class="page-content page-content--fluid">
        <div class="account__block-list">
          {%- for block in section.blocks -%}
            <div class="account__block-item" {{ block.shopify_attributes }}>
              {%- case block.type -%}
                {%- when '@app' -%}
                  {%- render block -%}

                {%- when 'liquid' -%}
                  {{- block.settings.liquid -}}
              {%- endcase -%}
            </div>
          {%- endfor -%}
        </div>
      </div>
    {%- else -%}
      <div class="page-header page-header--small">
        <div class="page-header__text-wrapper text-container">
          <h1 class="nbd-heading-h1">{{ 'customer.orders.title' | t }} <span class="bubble-count bubble-count--top">{{ customer.orders.size }}</span></h1>
        </div>
      </div>

      <div class="page-content page-content--fluid">
        <div class="account__block-list">
          {%- for block in section.blocks -%}
            <div class="account__block-item" {{ block.shopify_attributes }}>
              {%- case block.type -%}
                {%- when '@app' -%}
                  {%- render block -%}

                {%- when 'liquid' -%}
                  {{- block.settings.liquid -}}

                {%- when 'order_history' -%}
                  <div class="nbd-orders-list">
                    {%- for order in customer.orders -%}
                      <div class="nbd-order-card">
                        <div class="nbd-order-card__header">
                          <div class="nbd-order-card__number">
                            <span class="nbd-order-card__label">{{ 'customer.orders.order_number' | t }}</span>
                            <a href="{{ order.customer_url }}" class="nbd-order-card__value">{{ order.name }}</a>
                          </div>
                          <div class="nbd-order-card__date">
                            <span class="nbd-order-card__label">{{ 'customer.orders.date' | t }}</span>
                            <span class="nbd-order-card__value">{{ order.created_at | date: format: 'date_at' }}</span>
                          </div>
                        </div>

                        <div class="nbd-order-card__body">
                          <div class="nbd-order-card__status">
                            <div class="nbd-order-card__status-item">
                              <span class="nbd-order-card__label">{{ 'customer.orders.payment_status' | t }}</span>
                              <span class="nbd-order-card__value nbd-order-card__status--{{ order.financial_status_label }}">{{ order.financial_status_label }}</span>
                            </div>
                            <div class="nbd-order-card__status-item">
                              <span class="nbd-order-card__label">{{ 'customer.orders.fulfillment_status' | t }}</span>
                              <span class="nbd-order-card__value nbd-order-card__status--{{ order.fulfillment_status_label }}">{{ order.fulfillment_status_label }}</span>
                            </div>
                          </div>

                          <div class="nbd-order-card__total">
                            <span class="nbd-order-card__label">{{ 'customer.orders.total' | t }}</span>
                            <span class="nbd-order-card__value">{{ order.total_price | money }}</span>
                          </div>
                        </div>
                      </div>
                    {%- endfor -%}
                  </div>

                  {%- if paginate.pages > 1 -%}
                    {%- render 'pagination', paginate: paginate -%}
                  {%- endif -%}
              {%- endcase -%}
            </div>
          {%- endfor -%}
        </div>
      </div>
    {%- endif -%}
  </div>
</div>
```

### 3.2 Add Account-Specific CSS

**File**: `assets/theme.css`

**Add to the end of the file:**

```css
/* =========================================================
   NASIR BOOK DEPOT - CUSTOMER ACCOUNT
   ========================================================= */

.nbd-account-container {
  max-width: var(--nbd-container-max-width);
}

.nbd-account-empty-text {
  font-size: 16px;
  color: rgb(var(--nbd-muted-gray));
  margin-bottom: var(--nbd-space-4);
}

.nbd-orders-list {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
}

.nbd-order-card {
  background: rgb(var(--nbd-white));
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--block-border-radius);
  padding: var(--nbd-space-5);
  transition: box-shadow 0.2s ease;
}

.nbd-order-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.nbd-order-card__header {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-3);
  padding-bottom: var(--nbd-space-4);
  border-bottom: 1px solid rgb(var(--nbd-border-color));
}

@media screen and (min-width: 741px) {
  .nbd-order-card__header {
    flex-direction: row;
    justify-content: space-between;
  }
}

.nbd-order-card__number,
.nbd-order-card__date {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-1);
}

.nbd-order-card__label {
  font-size: 12px;
  font-weight: 600;
  color: rgb(var(--nbd-muted-gray));
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.nbd-order-card__value {
  font-size: 14px;
  font-weight: 500;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-order-card__value[href] {
  color: rgb(var(--nbd-primary-green));
  text-decoration: none;
}

.nbd-order-card__value[href]:hover {
  text-decoration: underline;
}

.nbd-order-card__body {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
  padding-top: var(--nbd-space-4);
}

@media screen and (min-width: 741px) {
  .nbd-order-card__body {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
}

.nbd-order-card__status {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-3);
}

@media screen and (min-width: 741px) {
  .nbd-order-card__status {
    flex-direction: row;
    gap: var(--nbd-space-6);
  }
}

.nbd-order-card__status-item {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-1);
}

.nbd-order-card__status--paid,
.nbd-order-card__status--fulfilled {
  color: rgb(var(--nbd-success-color));
}

.nbd-order-card__status--pending,
.nbd-order-card__status--unfulfilled {
  color: rgb(var(--nbd-gold-accent));
}

.nbd-order-card__status--refunded,
.nbd-order-card__status--partially_refunded {
  color: rgb(var(--nbd-error-color));
}

.nbd-order-card__total {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-1);
  text-align: right;
}

@media screen and (min-width: 741px) {
  .nbd-order-card__total {
    min-width: 120px;
  }
}

.nbd-order-card__total .nbd-order-card__value {
  font-size: 18px;
  font-weight: 700;
}
```

---

## 4. Contact Page Redesign

### 4.1 Update Contact Section

**File**: `sections/contact-form.liquid`

**Replace the custom styling section (lines 40-150) with standardized approach:**

```liquid
<style>
  #shopify-section-{{ section.id }} {
    --heading-color: {{ heading_color.red }}, {{ heading_color.green }}, {{ heading_color.blue }};
    --text-color: {{ text_color.red }}, {{ text_color.green }}, {{ text_color.blue }};
    --primary-button-background: {{ button_background.red }}, {{ button_background.green }}, {{ button_background.blue }};
    --primary-button-text-color: {{ button_text_color.red }}, {{ button_text_color.green }}, {{ button_text_color.blue }};
    --section-background: {{ section_background.red }}, {{ section_background.green }}, {{ section_background.blue }};
  }

  #shopify-section-{{ section.id }} .nbd-contact-page {
    background: rgb(var(--section-background));
    color: rgb(var(--text-color));
  }

  #shopify-section-{{ section.id }} .nbd-contact__container {
    max-width: var(--nbd-container-max-width);
    margin: 0 auto;
    padding: var(--vertical-breather) var(--nbd-container-gutter-mobile);
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-contact__container {
      padding: var(--vertical-breather) var(--nbd-container-gutter-tablet);
    }
  }

  @media screen and (min-width: 1200px) {
    #shopify-section-{{ section.id }} .nbd-contact__container {
      padding: var(--vertical-breather) var(--nbd-container-gutter-desktop);
    }
  }

  #shopify-section-{{ section.id }} .nbd-contact__grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--nbd-space-8);
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-contact__grid {
      grid-template-columns: 1fr 1fr;
    }
  }

  #shopify-section-{{ section.id }} .nbd-contact__info {
    display: flex;
    flex-direction: column;
    gap: var(--nbd-space-5);
  }

  #shopify-section-{{ section.id }} .nbd-contact__title {
    font-size: var(--nbd-h1-mobile);
    line-height: 1.1;
    font-weight: 700;
    color: rgb(var(--heading-color));
    margin-bottom: var(--nbd-space-3);
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-contact__title {
      font-size: var(--nbd-h1-tablet);
    }
  }

  @media screen and (min-width: 1200px) {
    #shopify-section-{{ section.id }} .nbd-contact__title {
      font-size: var(--nbd-h1-desktop);
    }
  }

  #shopify-section-{{ section.id }} .nbd-contact__intro {
    font-size: 16px;
    line-height: 1.6;
    color: rgb(var(--text-color));
  }

  #shopify-section-{{ section.id }} .nbd-contact-info-card {
    background: rgb(var(--secondary-background));
    border: 1px solid rgb(var(--border-color));
    border-radius: var(--block-border-radius);
    padding: var(--nbd-space-5);
  }

  #shopify-section-{{ section.id }} .nbd-contact-form-card {
    background: rgb(var(--secondary-background));
    border: 1px solid rgb(var(--border-color));
    border-radius: var(--block-border-radius);
    padding: var(--nbd-space-6);
  }
</style>

<section class="section nbd-contact-page">
  <div class="nbd-contact__container">
    <div class="nbd-contact__grid">
      <div class="nbd-contact__info">
        <h1 class="nbd-contact__title">{{ section.settings.title | default: 'Contact Nasir Book Depot' }}</h1>
        
        {%- if section.settings.content != blank -%}
          <div class="nbd-contact__intro">
            {{ section.settings.content }}
          </div>
        {%- endif -%}

        <div class="nbd-contact-info-card">
          {%- if section.settings.phone_number_1 != blank -%}
            <div class="nbd-contact-info-item">
              <span class="nbd-contact-info-label">{{ 'contact.phone' | t }}</span>
              <a href="tel:{{ section.settings.phone_number_1 | replace: ' ', '' }}" class="nbd-contact-info-value">{{ section.settings.phone_number_1 }}</a>
            </div>
          {%- endif -%}

          {%- if section.settings.email != blank -%}
            <div class="nbd-contact-info-item">
              <span class="nbd-contact-info-label">{{ 'contact.email' | t }}</span>
              <a href="mailto:{{ section.settings.email }}" class="nbd-contact-info-value">{{ section.settings.email }}</a>
            </div>
          {%- endif -%}

          {%- if section.settings.address != blank -%}
            <div class="nbd-contact-info-item">
              <span class="nbd-contact-info-label">{{ 'contact.address' | t }}</span>
              <address class="nbd-contact-info-value">{{ section.settings.address }}</address>
            </div>
          {%- endif -%}
        </div>

        <div class="nbd-contact__actions">
          {%- if section.settings.phone_number_1 != blank -%}
            <a href="tel:{{ section.settings.phone_number_1 | replace: ' ', '' }}" class="nbd-button--primary">{{ 'contact.call' | t }}</a>
          {%- endif -%}
          
          {%- if section.settings.directions_address != blank -%}
            <a href="{{ directions_url }}" target="_blank" rel="noopener" class="nbd-button--secondary">{{ 'contact.directions' | t }}</a>
          {%- endif -%}
        </div>
      </div>

      <div class="nbd-contact__form-wrapper">
        <div class="nbd-contact-form-card">
          <h2 class="nbd-heading-h3">{{ 'contact.form_title' | t }}</h2>
          
          {%- form 'contact', class: 'nbd-contact-form' -%}
            {%- if form.posted_successfully? -%}
              <div class="nbd-form-success">
                {{ 'contact.success' | t }}
              </div>
            {%- endif -%}

            {%- if form.errors -%}
              <div class="nbd-form-error">
                {{ form.errors | default_errors }}
              </div>
            {%- endif -%}

            <div class="nbd-form-field">
              <label for="contact-name" class="nbd-form-label">{{ 'contact.name' | t }}</label>
              <input type="text" id="contact-name" name="contact[name]" class="nbd-form-input" required>
            </div>

            <div class="nbd-form-field">
              <label for="contact-email" class="nbd-form-label">{{ 'contact.email' | t }}</label>
              <input type="email" id="contact-email" name="contact[email]" class="nbd-form-input" required>
            </div>

            <div class="nbd-form-field">
              <label for="contact-message" class="nbd-form-label">{{ 'contact.message' | t }}</label>
              <textarea id="contact-message" name="contact[body]" class="nbd-form-textarea" rows="5" required></textarea>
            </div>

            <button type="submit" class="nbd-button--primary nbd-button--full">{{ 'contact.send' | t }}</button>
          {%- endform -%}
        </div>
      </div>
    </div>
  </div>
</section>
```

### 4.2 Add Contact-Specific CSS

**File**: `assets/theme.css`

**Add to the end of the file:**

```css
/* =========================================================
   NASIR BOOK DEPOT - CONTACT PAGE
   ========================================================= */

.nbd-contact-page {
  background: rgb(var(--background));
}

.nbd-contact__info {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-5);
}

.nbd-contact__intro {
  font-size: 16px;
  line-height: 1.6;
  color: rgb(var(--text-color));
}

.nbd-contact-info-card {
  background: rgb(var(--secondary-background));
  border: 1px solid rgb(var(--border-color));
  border-radius: var(--block-border-radius);
  padding: var(--nbd-space-5);
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
}

.nbd-contact-info-item {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-1);
}

.nbd-contact-info-label {
  font-size: 12px;
  font-weight: 600;
  color: rgb(var(--nbd-muted-gray));
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.nbd-contact-info-value {
  font-size: 16px;
  color: rgb(var(--text-color));
  text-decoration: none;
}

.nbd-contact-info-value[href]:hover {
  color: rgb(var(--nbd-primary-green));
  text-decoration: underline;
}

.nbd-contact-info-value address {
  font-style: normal;
}

.nbd-contact__actions {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-3);
}

@media screen and (min-width: 741px) {
  .nbd-contact__actions {
    flex-direction: row;
  }
}

.nbd-contact-form-card {
  background: rgb(var(--secondary-background));
  border: 1px solid rgb(var(--border-color));
  border-radius: var(--block-border-radius);
  padding: var(--nbd-space-6);
}

.nbd-contact-form {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
}

.nbd-form-field {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-2);
}

.nbd-form-label {
  font-size: 14px;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-form-input,
.nbd-form-textarea {
  width: 100%;
  padding: var(--nbd-space-3);
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--button-border-radius);
  font-size: 16px;
  font-family: inherit;
  background: rgb(var(--nbd-white));
  color: rgb(var(--nbd-dark-gray));
}

.nbd-form-input:focus,
.nbd-form-textarea:focus {
  outline: 2px solid rgb(var(--nbd-primary-green));
  outline-offset: 2px;
}

.nbd-form-textarea {
  min-height: 120px;
  resize: vertical;
}

.nbd-form-success {
  background: rgba(var(--nbd-success-color), 0.1);
  color: rgb(var(--nbd-success-color));
  padding: var(--nbd-space-3);
  border-radius: var(--button-border-radius);
  font-size: 14px;
  text-align: center;
}

.nbd-form-error {
  background: rgba(var(--nbd-error-color), 0.1);
  color: rgb(var(--nbd-error-color));
  padding: var(--nbd-space-3);
  border-radius: var(--button-border-radius);
  font-size: 14px;
  text-align: center;
}
```

---

## 5. FAQ Page Redesign

### 5.1 Update FAQ Section

**File**: `sections/faq.liquid`

**Replace the FAQ item structure (lines 66-89) with enhanced styling:**

```liquid
<div class="faq__wrapper" itemscope itemtype="https://schema.org/FAQPage">
  {%- for block in section.blocks -%}
    {%- case block.type -%}
      {%- when 'category' -%}
        <h2 id="category-{{ section.id }}-{{ block.id }}" class="nbd-faq-category heading h6 anchor" {{ block.shopify_attributes }}>
          {{- block.settings.title |  escape -}}
        </h2>

      {%- when 'question' -%}
        <div class="nbd-faq-item" itemscope itemprop="mainEntity" itemtype="https://schema.org/Question">
          <button is="toggle-button" class="nbd-faq-question" aria-controls="block-{{ section.id }}-{{ block.id }}" aria-expanded="false" itemprop="name">
            <span>{{- block.settings.title -}}</span>
            <span class="nbd-faq-icon"></span>
          </button>

          <collapsible-content id="block-{{ section.id }}-{{ block.id }}" class="nbd-faq-answer anchor" itemscope itemprop="acceptedAnswer" itemtype="https://schema.org/Answer" {{ block.shopify_attributes }}>
            <div class="nbd-faq-answer-content text-container" itemprop="text">
              {{ block.settings.answer }}
            </div>
          </collapsible-content>
        </div>
    {%- endcase -%}
  {%- endfor -%}
</div>
```

### 5.2 Add FAQ-Specific CSS

**File**: `assets/theme.css`

**Add to the end of the file:**

```css
/* =========================================================
   NASIR BOOK DEPOT - FAQ PAGE
   ========================================================= */

.nbd-faq-category {
  font-size: var(--nbd-h4-mobile);
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-4);
  margin-top: var(--nbd-space-6);
}

@media screen and (min-width: 741px) {
  .nbd-faq-category {
    font-size: var(--nbd-h4-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-faq-category {
    font-size: var(--nbd-h4-desktop);
  }
}

.nbd-faq-item {
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--block-border-radius);
  margin-bottom: var(--nbd-space-3);
  overflow: hidden;
  background: rgb(var(--nbd-white));
  transition: box-shadow 0.2s ease;
}

.nbd-faq-item:hover {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.nbd-faq-question {
  width: 100%;
  background: rgb(var(--nbd-white));
  padding: var(--nbd-space-4) var(--nbd-space-5);
  font-size: 16px;
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  text-align: left;
  border: none;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: var(--nbd-space-3);
  transition: background-color 0.2s ease;
}

.nbd-faq-question:hover {
  background: rgb(var(--nbd-cream-bg));
}

.nbd-faq-question[aria-expanded="true"] {
  background: rgb(var(--nbd-cream-bg));
}

.nbd-faq-icon {
  width: 20px;
  height: 20px;
  position: relative;
  flex-shrink: 0;
}

.nbd-faq-icon::before,
.nbd-faq-icon::after {
  content: '';
  position: absolute;
  background: rgb(var(--nbd-primary-green));
  transition: transform 0.2s ease;
}

.nbd-faq-icon::before {
  width: 2px;
  height: 12px;
  left: 9px;
  top: 4px;
}

.nbd-faq-icon::after {
  width: 12px;
  height: 2px;
  left: 4px;
  top: 9px;
}

.nbd-faq-question[aria-expanded="true"] .nbd-faq-icon::before {
  transform: rotate(90deg);
}

.nbd-faq-answer {
  background: rgb(var(--nbd-cream-bg));
  border-top: 1px solid rgb(var(--nbd-border-color));
}

.nbd-faq-answer-content {
  padding: var(--nbd-space-5);
  font-size: 15px;
  line-height: 1.6;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-faq-answer-content a {
  color: rgb(var(--nbd-primary-green));
  text-decoration: underline;
}

.nbd-faq-answer-content a:hover {
  color: rgb(var(--nbd-gold-accent));
}
```

---

## 6. Policy Pages Redesign

### 6.1 Update Page Section

**File**: `sections/main-page.liquid`

**Replace the entire section with enhanced structure:**

```liquid
<section class="nbd-policy-page">
  <div class="container nbd-policy-container">
    <div class="page-header">
      <nav aria-label="{{ 'general.breadcrumb.title' | t }}" class="breadcrumb breadcrumb--floating text--xsmall hidden-phone">
        <ol class="breadcrumb__list" role="list">
          <li class="breadcrumb__item">
            <a class="breadcrumb__link" href="{{ routes.root_url }}">{{ 'general.breadcrumb.home' | t }}</a>
          </li>

          <li class="breadcrumb__item">
            <span class="breadcrumb__link" aria-current="page">{{ page.title }}</span>
          </li>
        </ol>
      </nav>

      <div class="page-header__text-wrapper text-container">
        {%- if section.settings.show_title -%}
          <h1 class="nbd-heading-h1">{{ page.title }}</h1>
        {%- endif -%}
      </div>
    </div>

    <div class="page-content page-content--{{ section.settings.page_width }} nbd-policy-content">
      {{- page.content -}}
    </div>
  </div>
</section>
```

### 6.2 Add Policy-Specific CSS

**File**: `assets/theme.css`

**Add to the end of the file:**

```css
/* =========================================================
   NASIR BOOK DEPOT - POLICY PAGES
   ========================================================= */

.nbd-policy-page {
  background: rgb(var(--background));
  padding: var(--vertical-breather) 0;
}

.nbd-policy-container {
  max-width: 800px;
}

.nbd-policy-content {
  font-size: 16px;
  line-height: 1.7;
  color: rgb(var(--nbd-dark-gray));
}

.nbd-policy-content h2 {
  font-size: var(--nbd-h3-mobile);
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-3);
  margin-top: var(--nbd-space-6);
}

@media screen and (min-width: 741px) {
  .nbd-policy-content h2 {
    font-size: var(--nbd-h3-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-policy-content h2 {
    font-size: var(--nbd-h3-desktop);
  }
}

.nbd-policy-content h3 {
  font-size: var(--nbd-h4-mobile);
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-2);
  margin-top: var(--nbd-space-4);
}

@media screen and (min-width: 741px) {
  .nbd-policy-content h3 {
    font-size: var(--nbd-h4-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-policy-content h3 {
    font-size: var(--nbd-h4-desktop);
  }
}

.nbd-policy-content h4 {
  font-size: var(--nbd-h5-mobile);
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-2);
  margin-top: var(--nbd-space-3);
}

@media screen and (min-width: 741px) {
  .nbd-policy-content h4 {
    font-size: var(--nbd-h5-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-policy-content h4 {
    font-size: var(--nbd-h5-desktop);
  }
}

.nbd-policy-content p {
  margin-bottom: var(--nbd-space-3);
}

.nbd-policy-content ul,
.nbd-policy-content ol {
  margin-left: var(--nbd-space-5);
  margin-bottom: var(--nbd-space-3);
}

.nbd-policy-content li {
  margin-bottom: var(--nbd-space-2);
}

.nbd-policy-content a {
  color: rgb(var(--nbd-primary-green));
  text-decoration: underline;
}

.nbd-policy-content a:hover {
  color: rgb(var(--nbd-gold-accent));
}

.nbd-policy-content strong,
.nbd-policy-content b {
  font-weight: 600;
}

.nbd-policy-content blockquote {
  border-left: 3px solid rgb(var(--nbd-gold-accent));
  padding-left: var(--nbd-space-4);
  margin: var(--nbd-space-4) 0;
  font-style: italic;
  color: rgb(var(--nbd-muted-gray));
}

.nbd-policy-content code {
  background: rgb(var(--nbd-cream-bg));
  padding: 2px 6px;
  border-radius: 2px;
  font-family: monospace;
  font-size: 14px;
}

.nbd-policy-content pre {
  background: rgb(var(--nbd-cream-bg));
  padding: var(--nbd-space-4);
  border-radius: var(--block-border-radius);
  overflow-x: auto;
  margin: var(--nbd-space-4) 0;
}

.nbd-policy-content pre code {
  background: none;
  padding: 0;
}
```

---

## 7. Wholesale Page Creation

### 7.1 Create Wholesale Section Files

**File**: `sections/wholesale-hero.liquid`

```liquid
{% schema %}
{
  "name": "Wholesale Hero",
  "settings": [
    {
      "type": "text",
      "id": "title",
      "label": "Title",
      "default": "Wholesale Partnerships"
    },
    {
      "type": "textarea",
      "id": "subtitle",
      "label": "Subtitle",
      "default": "Partner with Nasir Book Depot for quality Islamic books, general books, and stationery at competitive wholesale prices."
    },
    {
      "type": "text",
      "id": "button_text",
      "label": "Button text",
      "default": "Contact Us"
    },
    {
      "type": "url",
      "id": "button_link",
      "label": "Button link",
      "default": "/pages/contact"
    }
  ],
  "presets": [
    {
      "name": "Wholesale Hero"
    }
  ]
}
{% endschema %}

<style>
  #shopify-section-{{ section.id }} .nbd-wholesale-hero {
    background: linear-gradient(135deg, rgb(var(--nbd-primary-green)), #1a3d2d);
    color: rgb(var(--nbd-white));
    padding: var(--vertical-breather) 0;
    text-align: center;
  }

  #shopify-section-{{ section.id }} .nbd-wholesale-hero__container {
    max-width: var(--nbd-container-max-width);
    margin: 0 auto;
    padding: 0 var(--nbd-container-gutter-mobile);
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-hero__container {
      padding: 0 var(--nbd-container-gutter-tablet);
    }
  }

  @media screen and (min-width: 1200px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-hero__container {
      padding: 0 var(--nbd-container-gutter-desktop);
    }
  }

  #shopify-section-{{ section.id }} .nbd-wholesale-hero__title {
    font-size: var(--nbd-h1-mobile);
    line-height: 1.1;
    font-weight: 700;
    margin-bottom: var(--nbd-space-4);
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-hero__title {
      font-size: var(--nbd-h1-tablet);
    }
  }

  @media screen and (min-width: 1200px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-hero__title {
      font-size: var(--nbd-h1-desktop);
    }
  }

  #shopify-section-{{ section.id }} .nbd-wholesale-hero__subtitle {
    font-size: 16px;
    line-height: 1.6;
    margin-bottom: var(--nbd-space-6);
    max-width: 700px;
    margin-left: auto;
    margin-right: auto;
  }
</style>

<section class="section section--flush nbd-wholesale-hero">
  <div class="nbd-wholesale-hero__container">
    <h1 class="nbd-wholesale-hero__title">{{ section.settings.title }}</h1>
    
    {%- if section.settings.subtitle != blank -%}
      <p class="nbd-wholesale-hero__subtitle">{{ section.settings.subtitle }}</p>
    {%- endif -%}

    {%- if section.settings.button_text != blank -%}
      <a href="{{ section.settings.button_link }}" class="nbd-button--secondary">{{ section.settings.button_text }}</a>
    {%- endif -%}
  </div>
</section>
```

**File**: `sections/wholesale-benefits.liquid`

```liquid
{% schema %}
{
  "name": "Wholesale Benefits",
  "settings": [
    {
      "type": "text",
      "id": "title",
      "label": "Section title",
      "default": "Why Buy Wholesale From Us"
    }
  ],
  "blocks": [
    {
      "type": "benefit",
      "name": "Benefit",
      "settings": [
        {
          "type": "text",
          "id": "title",
          "label": "Title",
          "default": "Competitive Pricing"
        },
        {
          "type": "textarea",
          "id": "description",
          "label": "Description",
          "default": "Wholesale rates that help you maximize your margins"
        }
      ]
    }
  ],
  "presets": [
    {
      "name": "Wholesale Benefits"
    }
  ]
}
{% endschema %}

<style>
  #shopify-section-{{ section.id }} .nbd-wholesale-benefits {
    padding: var(--vertical-breather) 0;
  }

  #shopify-section-{{ section.id }} .nbd-wholesale-benefits__container {
    max-width: var(--nbd-container-max-width);
    margin: 0 auto;
    padding: 0 var(--nbd-container-gutter-mobile);
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-benefits__container {
      padding: 0 var(--nbd-container-gutter-tablet);
    }
  }

  @media screen and (min-width: 1200px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-benefits__container {
      padding: 0 var(--nbd-container-gutter-desktop);
    }
  }

  #shopify-section-{{ section.id }} .nbd-wholesale-benefits__title {
    font-size: var(--nbd-h2-mobile);
    font-weight: 700;
    color: rgb(var(--nbd-dark-gray));
    margin-bottom: var(--nbd-space-6);
    text-align: center;
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-benefits__title {
      font-size: var(--nbd-h2-tablet);
    }
  }

  @media screen and (min-width: 1200px) {
    #shopify-section-{{ section.id }} .nbd-wholesale-benefits__title {
      font-size: var(--nbd-h2-desktop);
    }
  }

  #shopify-section-{{ section.id }} .nbd-benefits-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--nbd-space-5);
  }

  @media screen and (min-width: 741px) {
    #shopify-section-{{ section.id }} .nbd-benefits-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media screen and (min-width: 1200px) {
    #shopify-section-{{ section.id }} .nbd-benefits-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }
</style>

<section class="section nbd-wholesale-benefits">
  <div class="nbd-wholesale-benefits__container">
    {%- if section.settings.title != blank -%}
      <h2 class="nbd-wholesale-benefits__title">{{ section.settings.title }}</h2>
    {%- endif -%}

    <div class="nbd-benefits-grid">
      {%- for block in section.blocks -%}
        <div class="nbd-benefit-card" {{ block.shopify_attributes }}>
          <h3 class="nbd-benefit-card__title">{{ block.settings.title }}</h3>
          <p class="nbd-benefit-card__description">{{ block.settings.description }}</p>
        </div>
      {%- endfor -%}
    </div>
  </div>
</section>
```

### 7.2 Create Wholesale Page Template

**File**: `templates/page.wholesale.json`

```json
{
  "sections": {
    "wholesale-hero": {
      "type": "wholesale-hero",
      "settings": {
        "title": "Wholesale Partnerships",
        "subtitle": "Partner with Nasir Book Depot for quality Islamic books, general books, and stationery at competitive wholesale prices.",
        "button_text": "Contact Us",
        "button_link": "/pages/contact"
      }
    },
    "wholesale-benefits": {
      "type": "wholesale-benefits",
      "blocks": [
        {
          "type": "benefit",
          "settings": {
            "title": "Competitive Pricing",
            "description": "Wholesale rates that help you maximize your margins"
          }
        },
        {
          "type": "benefit",
          "settings": {
            "title": "Quality Products",
            "description": "Curated selection of Islamic books, general books, and stationery"
          }
        },
        {
          "type": "benefit",
          "settings": {
            "title": "Reliable Service",
            "description": "Prompt delivery and dedicated customer support"
          }
        },
        {
          "type": "benefit",
          "settings": {
            "title": "Flexible Orders",
            "description": "No minimum order requirements for most products"
          }
        },
        {
          "type": "benefit",
          "settings": {
            "title": "Bulk Discounts",
            "description": "Additional savings on large quantity orders"
          }
        },
        {
          "type": "benefit",
          "settings": {
            "title": "Established 1988",
            "description": "Over 30 years of trusted service to the community"
          }
        }
      ]
    }
  },
  "order": [
    "wholesale-hero",
    "wholesale-benefits"
  ]
}
```

### 7.3 Add Wholesale CSS

**File**: `assets/theme.css`

**Add to the end of the file:**

```css
/* =========================================================
   NASIR BOOK DEPOT - WHOLESALE PAGE
   ========================================================= */

.nbd-benefit-card {
  background: rgb(var(--nbd-white));
  border: 1px solid rgb(var(--nbd-border-color));
  border-radius: var(--block-border-radius);
  padding: var(--nbd-space-5);
  text-align: center;
  transition: box-shadow 0.2s ease;
}

.nbd-benefit-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.nbd-benefit-card__title {
  font-size: var(--nbd-h4-mobile);
  font-weight: 600;
  color: rgb(var(--nbd-dark-gray));
  margin-bottom: var(--nbd-space-2);
}

@media screen and (min-width: 741px) {
  .nbd-benefit-card__title {
    font-size: var(--nbd-h4-tablet);
  }
}

@media screen and (min-width: 1200px) {
  .nbd-benefit-card__title {
    font-size: var(--nbd-h4-desktop);
  }
}

.nbd-benefit-card__description {
  font-size: 15px;
  line-height: 1.5;
  color: rgb(var(--nbd-muted-gray));
}
```

---

## 8. Mobile & Accessibility CSS Additions

### 8.1 Mobile Optimization

**File**: `assets/theme.css`

**Add mobile-specific improvements:**

```css
/* =========================================================
   MOBILE OPTIMIZATIONS
   ========================================================= */

@media screen and (max-width: 740px) {
  /* Ensure minimum touch targets */
  .nbd-button--primary,
  .nbd-button--secondary,
  .nbd-button--text {
    min-height: 44px;
    min-width: 44px;
  }

  /* Improve mobile spacing */
  .nbd-cart-item-card {
    padding: var(--nbd-space-4);
  }

  .nbd-order-card {
    padding: var(--nbd-space-4);
  }

  .nbd-contact-form-card {
    padding: var(--nbd-space-4);
  }

  /* Optimize mobile typography */
  .nbd-heading-h1 {
    font-size: 32px;
  }

  .nbd-heading-h2 {
    font-size: 28px;
  }

  .nbd-heading-h3 {
    font-size: 24px;
  }

  /* Improve mobile forms */
  .nbd-form-input,
  .nbd-form-textarea {
    font-size: 16px; /* Prevent iOS zoom */
  }
}
```

### 8.2 Accessibility Improvements

**File**: `assets/theme.css`

**Add accessibility enhancements:**

```css
/* =========================================================
   ACCESSIBILITY IMPROVEMENTS
   ========================================================= */

/* Focus indicators */
.nbd-button--primary:focus,
.nbd-button--secondary:focus,
.nbd-button--text:focus,
.nbd-form-input:focus,
.nbd-form-textarea:focus,
.nbd-faq-question:focus {
  outline: 2px solid rgb(var(--nbd-primary-green));
  outline-offset: 2px;
}

/* Skip links */
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: rgb(var(--nbd-primary-green));
  color: rgb(var(--nbd-white));
  padding: 8px 16px;
  z-index: 100;
  transition: top 0.2s ease;
}

.skip-link:focus {
  top: 0;
}

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  .nbd-button--primary,
  .nbd-button--secondary {
    border-width: 3px;
  }

  .nbd-card,
  .nbd-cart-item-card,
  .nbd-order-card {
    border-width: 2px;
  }
}
```

---

## 9. Implementation Checklist

### Phase 1: Foundation (Week 1)
- [ ] Add design system CSS variables to `css-variables.liquid`
- [ ] Add design system CSS classes to `theme.css`
- [ ] Update Cart page section and CSS
- [ ] Update Customer Account pages section and CSS
- [ ] Test on all devices

### Phase 2: Content Pages (Week 2)
- [ ] Update Contact page section and CSS
- [ ] Update FAQ page section and CSS
- [ ] Update Policy pages section and CSS
- [ ] Create Wholesale page sections
- [ ] Create Wholesale page template
- [ ] Test on all devices

### Phase 3: Refinement (Week 3)
- [ ] Add mobile optimization CSS
- [ ] Add accessibility improvements
- [ ] Cross-browser testing
- [ ] Performance optimization
- [ ] Final testing and validation

### Phase 4: Launch (Week 4)
- [ ] Deploy to production
- [ ] Monitor performance
- [ ] Gather user feedback
- [ ] Make final adjustments

---

## 10. Testing Checklist

### Visual Testing
- [ ] All pages use consistent typography
- [ ] All buttons follow standard system
- [ ] All cards use unified design
- [ ] Spacing is consistent across pages
- [ ] Colors match brand palette

### Functional Testing
- [ ] Cart functions correctly
- [ ] Customer account pages work
- [ ] Contact form submits properly
- [ ] FAQ accordions function
- [ ] Navigation works on all pages

### Mobile Testing
- [ ] Layouts work on mobile (320px-740px)
- [ ] Touch targets are sufficient
- [ ] Typography is readable
- [ ] Forms are easy to use
- [ ] Navigation is accessible

### Accessibility Testing
- [ ] Keyboard navigation works
- [ ] Screen reader compatibility
- [ ] Color contrast meets WCAG AA
- [ ] Focus indicators are visible
- [ ] ARIA labels are present

### Cross-Browser Testing
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)
- [ ] Mobile browsers

---

## Conclusion

This implementation guide provides exact code changes needed to achieve visual consistency across all pages of the Nasir Book Depot Shopify store. Follow the prioritized implementation plan and testing checklist to ensure successful deployment.

**Remember to:**
1. Backup your theme before making changes
2. Test changes on a development theme first
3. Monitor performance after deployment
4. Gather user feedback for continuous improvement

---

**Document Version**: 1.0  
**Last Updated**: August 28, 2026  
**Theme**: Focal by Maestrooo v9.0.0