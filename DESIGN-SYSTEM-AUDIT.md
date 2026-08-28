# Nasir Book Depot - Design System Audit & Redesign Guide

## Executive Summary

This document provides a complete visual and UX consistency audit of the Nasir Book Depot Shopify store, along with a unified design system and page-by-page redesign recommendations to ensure all pages match the Home Page design language.

**Theme**: Focal by Maestrooo (v9.0.0)  
**Analysis Date**: August 28, 2026  
**Brand**: Nasir Book Depot - Professional Bookstore

---

## 1. Design Audit Findings

### Current State Analysis

#### Homepage Design Language (Reference Standard)
The homepage establishes the design reference with these key characteristics:

**Visual Identity:**
- Warm, professional bookstore aesthetic
- Trustworthy and established feel
- Academic yet accessible
- Culturally rich and inclusive

**Color System:**
- Primary Green: #1F4D3A (Header, Primary Buttons)
- Dark Gray: #1F2933 (Headings, Body Text, Footer Background)
- Golden Accent: #C49A45 (Secondary Buttons, Stars, Highlights)
- Cream Background: #FAF7F0 (Main Background)
- White: #FFFFFF (Secondary Background, Cards)
- Success: #2E9E7B
- Error: #DE2A2A
- Terracotta: #B85C38 (Sale Accent)

**Typography:**
- Font Family: DM Sans
- Heading sizes scale responsively from 16px to 72px
- Body text: 14-16px base size
- Clean, highly readable for students and general customers

**Layout System:**
- Container max-width: 1600px
- Container gutters: 24px (mobile), 40px (tablet+)
- Grid system: 10 columns (mobile), 20 columns (desktop)
- Vertical spacing: 28-90px depending on settings
- Border radius: 0px (sharp, professional look)

**Component Style:**
- Product cards: Square images, minimal borders
- Buttons: Sharp corners (0px radius), 48-52px height
- Icons: 2px stroke width, outline style
- Shadows: Minimal, professional

---

### Consistency Issues Identified

#### HIGH PRIORITY ISSUES

**1. Inconsistent Spacing Systems**
- **Problem**: Different pages use different vertical spacing values
- **Impact**: Creates visual disconnection between pages
- **Affected Pages**: Cart, Customer Account, Policy pages, FAQ
- **Current State**: Some pages use `--vertical-breather`, others use custom padding
- **Solution**: Standardize all pages to use `--vertical-breather` system

**2. Typography Inconsistencies**
- **Problem**: Heading sizes vary across pages
- **Impact**: Reduced visual hierarchy and brand consistency
- **Affected Pages**: Cart page uses H2 for main title, About Us uses H1, Contact uses custom sizing
- **Current State**: 
  - Cart: `heading h2` (28-32px)
  - About Us: Custom clamp sizing (2.4rem to 5.4rem)
  - Contact: Custom clamp sizing (2.4rem to 5.4rem)
  - Policy pages: `heading h2` (28-32px)
- **Solution**: Create unified typography scale

**3. Button Style Variations**
- **Problem**: Different button styles across pages
- **Impact**: Confusing user experience, inconsistent CTAs
- **Affected Pages**: Cart, Contact, About Us
- **Current State**:
  - Homepage: Primary green (#1F4D3A), white text, 0px radius
  - Cart: Mixed primary/secondary buttons
  - Contact: Custom button styles
  - About Us: Custom styled buttons with arrows
- **Solution**: Standardize button system

**4. Card Design Inconsistencies**
- **Problem**: Different card styles, borders, and shadows
- **Impact**: Lack of visual cohesion
- **Affected Pages**: Contact info cards, Product cards, Account cards
- **Current State**:
  - Homepage: Minimal borders, white backgrounds
  - Contact: Custom bordered cards with shadows
  - Account: Basic table layouts
- **Solution**: Unified card component system

#### MEDIUM PRIORITY ISSUES

**5. Color Application Inconsistencies**
- **Problem**: Not all pages use brand colors consistently
- **Impact**: diluted brand identity
- **Affected Pages**: Policy pages, FAQ, Customer Account
- **Current State**: Some pages inherit theme colors, others use custom overrides
- **Solution**: Enforce brand color palette across all pages

**6. Layout Container Variations**
- **Problem**: Different container widths and gutters
- **Impact**: Inconsistent content width and reading experience
- **Affected Pages**: Contact (1320px max), About Us (custom), others use theme defaults
- **Solution**: Standardize container system

**7. Mobile Experience Inconsistencies**
- **Problem**: Different mobile layouts and breakpoints
- **Impact**: Inconsistent mobile experience
- **Affected Pages**: Cart, Account, Contact
- **Current State**: Some pages have custom mobile CSS, others rely on theme defaults
- **Solution**: Unified mobile-first approach

#### LOW PRIORITY ISSUES

**8. Icon Style Variations**
- **Problem**: Some sections use different icon sizes/strokes
- **Impact**: Minor visual inconsistency
- **Solution**: Enforce 2px stroke width consistently

**9. Form Design Variations**
- **Problem**: Contact form vs other forms have different styling
- **Impact**: Minor UX inconsistency
- **Solution**: Standardize form components

---

## 2. Unified Design System

### 2.1 Color Palette

```css
/* Brand Colors */
--nbd-primary-green: #1F4D3A;
--nbd-dark-gray: #1F2933;
--nbd-gold-accent: #C49A45;
--nbd-cream-bg: #FAF7F0;
--nbd-white: #FFFFFF;

/* Functional Colors */
--nbd-success: #2E9E7B;
--nbd-error: #DE2A2A;
--nbd-terracotta: #B85C38;
--nbd-muted-gray: #4E5964;
--nbd-border-color: #E7DFD2;

/* Text Colors */
--nbd-heading-color: #1F2933;
--nbd-body-color: #1F2933;
--nbd-muted-color: #4E5964;

/* Component Colors */
--nbd-button-primary-bg: #1F4D3A;
--nbd-button-primary-text: #FFFFFF;
--nbd-button-secondary-bg: #C49A45;
--nbd-button-secondary-text: #1F2933;
--nbd-card-bg: #FFFFFF;
--nbd-card-border: #E7DFD2;
```

### 2.2 Typography System

```css
/* Font Family */
--nbd-font-family: 'DM Sans', sans-serif;

/* Heading Scale */
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

/* Body Text */
--nbd-body-large-desktop: 18px;
--nbd-body-large-mobile: 16px;

--nbd-body-regular-desktop: 16px;
--nbd-body-regular-mobile: 14px;

--nbd-body-small-desktop: 14px;
--nbd-body-small-mobile: 12px;

/* Specialized Typography */
--nbd-caption: 12px;
--nbd-button-text: 14px;
--nbd-navigation: 14px;
--nbd-product-title: 16px;
```

### 2.3 Spacing System

```css
/* Base Spacing Scale */
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

/* Section Spacing */
--nbd-section-spacing-mobile: 48px;
--nbd-section-spacing-tablet: 64px;
--nbd-section-spacing-desktop: 80px;

/* Component Spacing */
--nbd-element-spacing-mobile: 24px;
--nbd-element-spacing-tablet: 32px;
--nbd-element-spacing-desktop: 40px;
```

### 2.4 Layout System

```css
/* Container System */
--nbd-container-max-width: 1320px;
--nbd-container-gutter-mobile: 20px;
--nbd-container-gutter-tablet: 32px;
--nbd-container-gutter-desktop: 40px;

/* Grid System */
--nbd-grid-columns-mobile: 2;
--nbd-grid-columns-tablet: 3;
--nbd-grid-columns-desktop: 4;

--nbd-grid-gap-mobile: 16px;
--nbd-grid-gap-tablet: 24px;
--nbd-grid-gap-desktop: 32px;
```

### 2.5 Border Radius System

```css
/* Button Radius */
--nbd-button-radius: 0px;

/* Card Radius */
--nbd-card-radius: 0px;

/* Input Radius */
--nbd-input-radius: 0px;

/* Badge/Label Radius */
--nbd-badge-radius: 0px;
```

### 2.6 Shadow System

```css
/* Card Shadow */
--nbd-card-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);

/* Card Hover Shadow */
--nbd-card-hover-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);

/* Dropdown Shadow */
--nbd-dropdown-shadow: 0 4px 16px rgba(0, 0, 0, 0.12);
```

### 2.7 Button System

#### Primary Button
```css
.nbd-button--primary {
  background-color: var(--nbd-primary-green);
  color: var(--nbd-white);
  border: 2px solid var(--nbd-primary-green);
  border-radius: var(--nbd-button-radius);
  padding: 14px 32px;
  font-size: var(--nbd-button-text);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  transition: all 0.2s ease;
}

.nbd-button--primary:hover {
  background-color: #1a3d2d;
  border-color: #1a3d2d;
}

.nbd-button--primary:focus {
  outline: 2px solid var(--nbd-gold-accent);
  outline-offset: 2px;
}
```

#### Secondary Button
```css
.nbd-button--secondary {
  background-color: var(--nbd-gold-accent);
  color: var(--nbd-dark-gray);
  border: 2px solid var(--nbd-gold-accent);
  border-radius: var(--nbd-button-radius);
  padding: 14px 32px;
  font-size: var(--nbd-button-text);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  transition: all 0.2s ease;
}

.nbd-button--secondary:hover {
  background-color: #b08a3d;
  border-color: #b08a3d;
}
```

#### Text Button
```css
.nbd-button--text {
  background-color: transparent;
  color: var(--nbd-primary-green);
  border: none;
  border-radius: var(--nbd-button-radius);
  padding: 8px 16px;
  font-size: var(--nbd-button-text);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  transition: all 0.2s ease;
}

.nbd-button--text:hover {
  color: var(--nbd-gold-accent);
  text-decoration: underline;
}
```

### 2.8 Card System

#### Standard Card
```css
.nbd-card {
  background-color: var(--nbd-card-bg);
  border: 1px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  box-shadow: var(--nbd-card-shadow);
  padding: var(--nbd-space-6);
  transition: box-shadow 0.2s ease;
}

.nbd-card:hover {
  box-shadow: var(--nbd-card-hover-shadow);
}
```

#### Product Card
```css
.nbd-product-card {
  background-color: var(--nbd-card-bg);
  border: 1px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  overflow: hidden;
  transition: box-shadow 0.2s ease;
}

.nbd-product-card:hover {
  box-shadow: var(--nbd-card-hover-shadow);
}

.nbd-product-card__image {
  aspect-ratio: 1/1;
  background-color: var(--nbd-cream-bg);
}

.nbd-product-card__content {
  padding: var(--nbd-space-4);
}
```

---

## 3. Page-by-Page Redesign Recommendations

### 3.1 Cart Page

#### Current Issues
- Inconsistent heading size (H2 instead of H1)
- Basic table layout lacks visual hierarchy
- Cart summary styling doesn't match homepage aesthetic
- Quantity controls are basic

#### Redesign Recommendations

**Layout Improvements:**
- Use main container with consistent spacing
- Implement card-based cart item design
- Add visual hierarchy with proper heading sizing
- Improve order summary with card styling

**Typography Updates:**
```css
.cart-page-title {
  font-size: var(--nbd-h2-desktop);
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-6);
}

.cart-item-title {
  font-size: var(--nbd-body-regular-desktop);
  font-weight: 600;
  color: var(--nbd-heading-color);
}

.cart-item-price {
  font-size: var(--nbd-body-regular-desktop);
  color: var(--nbd-body-color);
}
```

**Card Design:**
```css
.cart-item-card {
  background: var(--nbd-card-bg);
  border: 1px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  padding: var(--nbd-space-5);
  margin-bottom: var(--nbd-space-4);
  display: grid;
  grid-template-columns: auto 1fr auto;
  gap: var(--nbd-space-4);
  align-items: center;
}
```

**Button Styling:**
```css
.cart-checkout-button {
  @extend .nbd-button--primary;
  width: 100%;
  margin-top: var(--nbd-space-5);
}
```

---

### 3.2 Customer Account Pages

#### Current Issues
- Basic table layouts lack visual polish
- Inconsistent heading sizes
- Navigation doesn't match homepage aesthetic
- Empty states are basic

#### Redesign Recommendations

**Dashboard Layout:**
- Implement card-based order display
- Add visual hierarchy with proper headings
- Improve navigation styling
- Enhanced empty states

**Order List Card:**
```css
.account-order-card {
  background: var(--nbd-card-bg);
  border: 1px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  padding: var(--nbd-space-5);
  margin-bottom: var(--nbd-space-4);
  transition: box-shadow 0.2s ease;
}

.account-order-card:hover {
  box-shadow: var(--nbd-card-hover-shadow);
}

.account-order-number {
  font-size: var(--nbd-h6-desktop);
  font-weight: 600;
  color: var(--nbd-primary-green);
  margin-bottom: var(--nbd-space-2);
}
```

**Navigation Styling:**
```css
.account-navigation {
  display: flex;
  gap: var(--nbd-space-6);
  padding-bottom: var(--nbd-space-4);
  border-bottom: 1px solid var(--nbd-card-border);
  margin-bottom: var(--nbd-space-6);
}

.account-nav-link {
  font-size: var(--nbd-body-regular-desktop);
  font-weight: 500;
  color: var(--nbd-muted-color);
  text-decoration: none;
  transition: color 0.2s ease;
}

.account-nav-link:hover,
.account-nav-link.active {
  color: var(--nbd-primary-green);
  text-decoration: underline;
}
```

---

### 3.3 About Us Page

#### Current Issues
- Custom sizing conflicts with theme system
- Inconsistent with homepage aesthetic
- Custom component styling breaks theme consistency

#### Redesign Recommendations

**Integrate with Theme System:**
- Use theme heading classes instead of custom sizing
- Apply brand colors consistently
- Use standard spacing system
- Maintain custom layout but with theme-consistent styling

**Typography Integration:**
```css
.about-page-title {
  @extend .heading h1;
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-5);
}

.about-section-heading {
  @extend .heading h3;
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-4);
}
```

**Button Standardization:**
```css
.about-button-primary {
  @extend .nbd-button--primary;
}

.about-button-secondary {
  @extend .nbd-button--secondary;
}
```

---

### 3.4 Contact Us Page

#### Current Issues
- Custom container width (1320px vs theme 1600px)
- Custom typography sizing
- Inconsistent card styling
- Custom color variables conflict with theme

#### Redesign Recommendations

**Standardize Container:**
```css
.contact-page-container {
  max-width: var(--nbd-container-max-width);
  margin: 0 auto;
  padding: 0 var(--nbd-container-gutter-mobile);
}

@media (min-width: 741px) {
  .contact-page-container {
    padding: 0 var(--nbd-container-gutter-tablet);
  }
}

@media (min-width: 1200px) {
  .contact-page-container {
    padding: 0 var(--nbd-container-gutter-desktop);
  }
}
```

**Typography Standardization:**
```css
.contact-page-title {
  @extend .heading h1;
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-4);
}

.contact-form-heading {
  @extend .heading h3;
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-4);
}
```

**Card Styling:**
```css
.contact-info-card {
  background: var(--nbd-card-bg);
  border: 1px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  padding: var(--nbd-space-5);
  margin-bottom: var(--nbd-space-4);
}
```

---

### 3.5 FAQ Page

#### Current Issues
- Basic accordion styling
- Inconsistent spacing
- Navigation styling doesn't match brand

#### Redesign Recommendations

**Enhanced Accordion Styling:**
```css
.faq-item {
  border: 1px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  margin-bottom: var(--nbd-space-3);
  overflow: hidden;
}

.faq-question {
  background: var(--nbd-card-bg);
  padding: var(--nbd-space-4) var(--nbd-space-5);
  font-size: var(--nbd-body-regular-desktop);
  font-weight: 600;
  color: var(--nbd-heading-color);
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.faq-answer {
  padding: var(--nbd-space-5);
  background: var(--nbd-cream-bg);
  border-top: 1px solid var(--nbd-card-border);
}
```

**Navigation Styling:**
```css
.faq-navigation {
  display: flex;
  gap: var(--nbd-space-6);
  padding-bottom: var(--nbd-space-4);
  border-bottom: 1px solid var(--nbd-card-border);
  margin-bottom: var(--nbd-space-6);
}

.faq-nav-link {
  font-size: var(--nbd-body-regular-desktop);
  font-weight: 500;
  color: var(--nbd-muted-color);
  text-decoration: none;
  transition: color 0.2s ease;
}

.faq-nav-link:hover,
.faq-nav-link.active {
  color: var(--nbd-primary-green);
  text-decoration: underline;
}
```

---

### 3.6 Policy Pages (Shipping, Returns, Privacy, Terms, Cookie)

#### Current Issues
- Basic typography lacks hierarchy
- Inconsistent spacing
- No visual hierarchy
- Plain text content

#### Redesign Recommendations

**Enhanced Typography:**
```css
.policy-page-title {
  @extend .heading h1;
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-6);
}

.policy-section-heading {
  @extend .heading h3;
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-3);
  margin-top: var(--nbd-space-6);
}

.policy-sub-heading {
  @extend .heading h4;
  color: var(--nbd-heading-color);
  margin-bottom: var(--nbd-space-2);
  margin-top: var(--nbd-space-4);
}
```

**Content Styling:**
```css
.policy-content {
  max-width: 800px;
  line-height: 1.7;
  color: var(--nbd-body-color);
}

.policy-content ul,
.policy-content ol {
  margin-left: var(--nbd-space-5);
  margin-bottom: var(--nbd-space-3);
}

.policy-content li {
  margin-bottom: var(--nbd-space-2);
}

.policy-content a {
  color: var(--nbd-primary-green);
  text-decoration: underline;
}

.policy-content a:hover {
  color: var(--nbd-gold-accent);
}
```

---

## 4. Wholesale Page Design

### 4.1 Page Structure

#### Hero Section
```css
.wholesale-hero {
  background: linear-gradient(135deg, var(--nbd-primary-green), #1a3d2d);
  color: var(--nbd-white);
  padding: var(--nbd-section-spacing-desktop) 0;
  text-align: center;
}

.wholesale-hero-title {
  @extend .heading h1;
  color: var(--nbd-white);
  margin-bottom: var(--nbd-space-4);
}

.wholesale-hero-subtitle {
  font-size: var(--nbd-body-large-desktop);
  margin-bottom: var(--nbd-space-6);
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}
```

#### Who We Serve Section
```css
.wholesale-serve-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--nbd-space-5);
  margin: var(--nbd-section-spacing-desktop) 0;
}

.wholesale-serve-card {
  background: var(--nbd-card-bg);
  border: 1px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  padding: var(--nbd-space-5);
  text-align: center;
  transition: box-shadow 0.2s ease;
}

.wholesale-serve-card:hover {
  box-shadow: var(--nbd-card-hover-shadow);
}
```

#### Categories Section
```css
.wholesale-categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: var(--nbd-space-4);
  margin: var(--nbd-section-spacing-desktop) 0;
}

.wholesale-category-item {
  background: var(--nbd-cream-bg);
  border: 2px solid var(--nbd-card-border);
  border-radius: var(--nbd-card-radius);
  padding: var(--nbd-space-4);
  text-align: center;
  font-weight: 600;
  color: var(--nbd-heading-color);
}
```

#### Ordering Process Section
```css
.wholesale-process-steps {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: var(--nbd-space-5);
  margin: var(--nbd-section-spacing-desktop) 0;
}

.wholesale-process-step {
  position: relative;
  padding-left: var(--nbd-space-6);
}

.wholesale-process-number {
  position: absolute;
  left: 0;
  top: 0;
  width: 40px;
  height: 40px;
  background: var(--nbd-gold-accent);
  color: var(--nbd-dark-gray);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
}
```

#### Contact Section
```css
.wholesale-contact-section {
  background: var(--nbd-cream-bg);
  padding: var(--nbd-section-spacing-desktop) 0;
  margin: var(--nbd-section-spacing-desktop) 0;
}

.wholesale-contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--nbd-space-8);
}

.wholesale-contact-info {
  display: flex;
  flex-direction: column;
  gap: var(--nbd-space-4);
}

.wholesale-contact-item {
  display: flex;
  align-items: center;
  gap: var(--nbd-space-3);
  font-size: var(--nbd-body-regular-desktop);
}
```

### 4.2 Template Structure

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
        }
      ]
    },
    "wholesale-serve": {
      "type": "wholesale-serve",
      "blocks": [
        {
          "type": "customer",
          "settings": {
            "name": "Schools",
            "icon": "school"
          }
        }
      ]
    },
    "wholesale-categories": {
      "type": "wholesale-categories",
      "settings": {
        "title": "Product Categories"
      }
    },
    "wholesale-process": {
      "type": "wholesale-process",
      "settings": {
        "title": "How It Works"
      }
    },
    "wholesale-contact": {
      "type": "wholesale-contact",
      "settings": {
        "title": "Get Started Today"
      }
    }
  },
  "order": [
    "wholesale-hero",
    "wholesale-benefits", 
    "wholesale-serve",
    "wholesale-categories",
    "wholesale-process",
    "wholesale-contact"
  ]
}
```

---

## 5. Mobile & Accessibility Recommendations

### 5.1 Mobile Optimization

**Touch Targets:**
- Minimum touch target size: 44px
- Button padding: 12px 24px on mobile
- Spacing between interactive elements: 8px minimum

**Mobile Layout:**
- Single column layouts for content sections
- Stacked card designs
- Simplified navigation
- Optimized form inputs

**Mobile Typography:**
- Base font size: 16px to prevent zooming
- Line height: 1.5 for readability
- Sufficient contrast ratios

### 5.2 Accessibility Standards

**Color Contrast:**
- Normal text: 4.5:1 minimum contrast ratio
- Large text: 3:1 minimum contrast ratio
- Interactive elements: 3:1 minimum contrast ratio

**Keyboard Navigation:**
- Tab order follows logical sequence
- Focus indicators visible (2px outline)
- Skip links for navigation
- ARIA labels for interactive elements

**Screen Reader Support:**
- Alt text for all images
- Proper heading hierarchy
- Semantic HTML structure
- ARIA landmarks for regions

**Form Accessibility:**
- Labels associated with inputs
- Error messages announced
- Required fields clearly marked
- Instructions provided

---

## 6. Implementation Priority

### HIGH PRIORITY (Week 1)
1. **Standardize Typography System** - Implement unified heading scale across all pages
2. **Fix Button Consistency** - Apply standard button styles to Cart, Contact, About Us
3. **Standardize Spacing** - Apply consistent vertical spacing system
4. **Card System Implementation** - Unified card designs across all pages

### MEDIUM PRIORITY (Week 2)
5. **Cart Page Redesign** - Implement card-based cart layout
6. **Customer Account Updates** - Improve account page styling
7. **Policy Page Enhancements** - Add visual hierarchy to policy pages
8. **FAQ Page Improvements** - Enhanced accordion styling

### LOW PRIORITY (Week 3)
9. **Contact Page Refinement** - Minor styling adjustments
10. **About Us Integration** - Better theme integration
11. **Mobile Polish** - Mobile experience refinements
12. **Accessibility Audit** - Final accessibility improvements

### NEW FEATURE (Week 4)
13. **Wholesale Page Creation** - Build new wholesale page from scratch

---

## 7. Shopify Implementation Notes

### 7.1 Theme Settings Configuration

Ensure these settings are configured in Shopify admin:

**Colors:**
- Heading: #1F2933
- Body text: #1F2933
- Background: #FAF7F0
- Secondary background: #FFFFFF
- Header background: #1F4D3A
- Header text: #FAF7F0
- Footer background: #1F2933
- Footer text: #FAF7F0
- Primary button background: #1F4D3A
- Primary button text: #FFFFFF
- Secondary button background: #C49A45
- Secondary button text: #1F2933

**Typography:**
- Heading font: DM Sans
- Text font: DM Sans
- Heading font size: Large
- Base font size: 16px

**Appearance:**
- Icon thickness: 2px
- Button/input border radius: 0
- Block border radius: None
- Vertical spacing: Large

### 7.2 CSS Variable Integration

Add these variables to the theme's CSS variable system:

```css
:root {
  /* Nasir Book Depot Brand Colors */
  --nbd-primary-green: 31, 77, 58;
  --nbd-dark-gray: 31, 41, 51;
  --nbd-gold-accent: 196, 154, 69;
  --nbd-cream-bg: 250, 247, 240;
  
  /* Typography Override */
  --nbd-h1-size: 62px;
  --nbd-h2-size: 54px;
  --nbd-h3-size: 40px;
  
  /* Spacing Override */
  --nbd-section-spacing: 80px;
  --nbd-element-spacing: 40px;
}
```

### 7.3 Section Modifications

**Modified Sections:**
- `main-cart.liquid` - Update cart layout and styling
- `main-customers-account.liquid` - Improve account page design
- `main-customers-addresses.liquid` - Enhance address management
- `contact-form.liquid` - Standardize contact page styling
- `faq.liquid` - Improve FAQ accordion design
- `main-page.liquid` - Enhance policy page typography

**New Sections:**
- `wholesale-hero.liquid` - Wholesale page hero section
- `wholesale-benefits.liquid` - Benefits showcase
- `wholesale-serve.liquid` - Customer types
- `wholesale-categories.liquid` - Product categories
- `wholesale-process.liquid` - Ordering process
- `wholesale-contact.liquid` - Contact section

### 7.4 Template Creation

**New Template:**
- `page.wholesale.json` - Wholesale page template

---

## 8. Testing & Validation

### 8.1 Cross-Device Testing
- Mobile (320px - 740px)
- Tablet (741px - 1199px)
- Desktop (1200px+)
- Large screens (1600px+)

### 8.2 Browser Testing
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

### 8.3 Accessibility Testing
- WAVE tool validation
- Keyboard navigation testing
- Screen reader testing (NVDA, VoiceOver)
- Color contrast validation

### 8.4 Performance Testing
- Page load speed
- Mobile performance
- Image optimization
- CSS optimization

---

## 9. Maintenance Guidelines

### 9.1 Design System Updates
- Document any deviations from the design system
- Regular audits for consistency
- Update documentation as changes are made
- Train team on design system usage

### 9.2 Theme Updates
- Test theme updates against custom modifications
- Maintain backup of custom sections
- Document any theme-specific customizations
- Plan for theme migration strategy

### 9.3 Content Guidelines
- Use defined typography scale
- Apply brand colors consistently
- Follow spacing system
- Use standardized components

---

## 10. Success Metrics

### 10.1 Design Consistency
- 100% pages use unified typography system
- 100% pages use consistent spacing
- 100% buttons follow standard system
- 100% cards use unified design

### 10.2 User Experience
- Improved navigation consistency
- Enhanced visual hierarchy
- Better mobile experience
- Increased accessibility compliance

### 10.3 Business Impact
- Improved conversion rates
- Reduced bounce rates
- Increased time on site
- Better customer satisfaction

---

## Conclusion

This design system audit provides a comprehensive roadmap for achieving visual consistency across all pages of the Nasir Book Depot Shopify store. By implementing the unified design system and following the page-by-page redesign recommendations, the store will achieve a cohesive, professional appearance that matches the homepage design language while maintaining the brand's trustworthy, academic bookstore identity.

The prioritized implementation plan ensures that high-impact changes are addressed first, with systematic improvements rolling out over a 4-week period. Regular testing and validation will ensure that all changes meet both design standards and accessibility requirements.

**Next Steps:**
1. Review and approve design system
2. Begin HIGH PRIORITY implementations
3. Create new Wholesale page
4. Conduct thorough testing
5. Launch and monitor performance

---

**Document Version**: 1.0  
**Last Updated**: August 28, 2026  
**Prepared For**: Nasir Book Depot  
**Theme**: Focal by Maestrooo v9.0.0