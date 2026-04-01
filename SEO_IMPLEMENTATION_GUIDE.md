# SEO Improvement Implementation Guide
## Hugo Project: demo-sadap

Quick reference guide for implementing the SEO improvements recommended in SEO_ANALYSIS_REPORT.md

---

## 1. FIX HEADING HIERARCHY (Critical)

**File:** `themes/hugo_framework/layouts/_default/single.html`  
**Line:** ~240  
**Issue:** H1 styled as H5, causing semantic issues

### Change From:
```html
<h1 class="h5">{{.Title}}</h1>
```

### Change To:
```html
<h2 class="h5">{{.Title}}</h2>
```

**Why:** Preserves visual appearance (h5 styling) while using correct semantic level (h2)

---

## 2. FIX TWITTER DESCRIPTION META TAG LOGIC (High Priority)

**File:** `themes/hugo_framework/layouts/partials/component/meta/data.html`  
**Line:** ~23  
**Issue:** Description fallback logic is broken

### Current Broken Code:
```html
<meta name="twitter:description" content="{{ if .Params.description | safeHTML }}{{ .Params.description | safeHTML }}{{else}}Tutorial terbaru {{.Title}} {{ now.Format "2006"}} - {{.Site.Title}}{{end}}" />
```

### Fixed Code:
```html
<meta name="twitter:description" content="{{ if .Params.description }}{{ .Params.description | safeHTML }}{{else}}Tutorial terbaru {{.Title}} {{ now.Format "2006"}} - {{.Site.Title}}{{end}}" />
```

**Change:** Remove `| safeHTML` from the if condition itself (it should only be in the output)

---

## 3. IMPLEMENT BREADCRUMB SCHEMA (High Priority)

**File:** `themes/hugo_framework/layouts/partials/component/meta/schema/breadcrumbs.json`  
**Current Status:** File exists but is empty

### Add This Content:

```json
{{ if .Parent }}
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "{{ .Site.BaseURL }}"
    }
    {{ $current := . }}
    {{ range .Breadcrumbs }}
    ,{
      "@type": "ListItem",
      "position": {{ add .Count 2 }},
      "name": "{{ .Title }}",
      "item": "{{ .Permalink }}"
    }
    {{ end }}
    ,{
      "@type": "ListItem",
      "position": {{ len .Breadcrumbs | add 2 }},
      "name": "{{ .Title }}",
      "item": "{{ .Permalink }}"
    }
  ]
}
</script>
{{ end }}
```

**Note:** This enables breadcrumb structure data for Google Search Console

---

## 4. ADD SEMANTIC HTML STRUCTURE (Medium Priority)

**File:** `themes/hugo_framework/layouts/_default/single.html`

### Update the body and main content area:

**Find this section:**
```html
<body class="page-header-fixed page-sidebar-closed-hide-logo page-content-white page-md">
<div class="page-wrapper">

<!-- NAV -->
{{ partial "demo/navigation" . }}
<!-- NAV -->


<div class="page-content-wrapper">

<div class="page-content">
```

### Replace with:
```html
<body class="page-header-fixed page-sidebar-closed-hide-logo page-content-white page-md">
<header class="page-wrapper">
  <!-- NAV -->
  <nav>
    {{ partial "demo/navigation" . }}
  </nav>
  <!-- NAV -->
</header>

<div class="page-content-wrapper">
  <main class="page-content">
```

**And at the end of the content, before footer:**

**Find:**
```html
{{ .Content }}

</div>

</div>

<!-- Footer -->
{{ partial "footer" . }}
```

**Replace with:**
```html
<article>
  {{ .Content }}
</article>

</main>

</div>

<!-- Footer -->
<footer>
  {{ partial "footer" . }}
</footer>
```

---

## 5. UPDATE FOOTER PARTIAL (Medium Priority)

**File:** `themes/hugo_framework/layouts/partials/footer.html`

**Find:**
```html
<div class="page-footer" style="height: 110px;">
    <div class="page-footer-inner">
```

**Replace with:**
```html
<div class="page-footer" style="height: 110px;" role="contentinfo">
    <div class="page-footer-inner">
```

**And at the very end, change:**
```html
</div>
</div>
```

If this is the last div, ensure it closes the footer tag instead.

---

## 6. ENHANCE IMAGE RENDERING (Medium Priority)

**File:** `themes/hugo_framework/layouts/_default/_markup/render-image.html`

**Current:**
```html
{{- $src := .Destination | safeURL -}}

{{- if strings.HasPrefix .Destination "http" -}}
<img class="img-fluid d-block mx-auto rounded mb-5 mt-5" src="{{ .Destination | safeURL }}" alt="{{ .Text }}" loading="lazy" />
{{- else -}}
<!-- Load image data with imageConfig and insert it with `<img>` -->       
{{- $config := imageConfig (printf "/static/%s" $src) -}}
<img class="img-fluid d-block mx-auto rounded mb-5 mt-5" src="{{ .Destination | safeURL }}" alt="{{ .Text | safeHTML }}" loading="lazy" height="{{$config.Height}}" width="{{$config.Width}}" />
{{- end -}}
```

**Enhanced version:**
```html
{{- $src := .Destination | safeURL -}}
{{- $altText := if .Text (printf "%s" .Text) "Image content" -}}

{{- if strings.HasPrefix .Destination "http" -}}
<img class="img-fluid d-block mx-auto rounded mb-5 mt-5" 
     src="{{ .Destination | safeURL }}" 
     alt="{{ $altText }}" 
     decoding="async"
     loading="lazy" />
{{- else -}}
<!-- Load image data with imageConfig and insert it with `<img>` -->       
{{- $config := imageConfig (printf "/static/%s" $src) -}}
<img class="img-fluid d-block mx-auto rounded mb-5 mt-5" 
     src="{{ .Destination | safeURL }}" 
     alt="{{ $altText }}" 
     decoding="async"
     loading="lazy" 
     height="{{$config.Height}}" 
     width="{{$config.Width}}" />
{{- end -}}
```

**Changes:**
- Added `decoding="async"` for performance
- Added fallback alt text: "Image content" when not provided
- Assigned alt text to variable for cleaner code

---

## 7. ENHANCE META TAGS WITH ARTICLE SCHEMA DATA

**File:** `themes/hugo_framework/layouts/partials/component/meta/data.html`

**Add after the Twitter Card section (after Twitter image tag), before favicon comment:**

```html
<!-- Article Publication Dates for Social Media -->
<meta property="article:published_time" content="{{ .Date.Format "2006-01-02T15:04:05Z07:00" }}">
<meta property="article:modified_time" content="{{ .Lastmod.Format "2006-01-02T15:04:05Z07:00" }}">

<!-- Article Authors and Tags -->
{{ range (.GetTerms "authors") }}
<meta property="article:author" content="{{ .LinkTitle | default .Site.Params.authors }}">
{{ end }}

{{ range (.GetTerms "tags") }}
<meta property="article:tag" content="{{ .Title }}">
{{ end }}
```

---

## 8. CREATE CUSTOM ROBOTS.TXT (Optional but Recommended)

**File:** `layouts/robots.txt` (create new file)

**Content:**
```
User-agent: *
Allow: /
Allow: /public/
Disallow: /admin/
Disallow: /search/
Disallow: /*.js$
Disallow: /*.css$
Disallow: /*?*
Allow: /?

# Specific bots
User-agent: MJ12bot
Disallow: /

User-agent: AhrefsBot
Disallow: /

Crawl-delay: 1

Sitemap: {{ .Site.BaseURL }}sitemap.xml
```

**Why:** Optimizes crawl budget and blocks aggressive bots

---

## 9. ADD MOBILE APP META TAGS (Optional)

**File:** `themes/hugo_framework/layouts/partials/component/meta/data.html`

**Add before favicon section:**

```html
<!-- Mobile App Meta Tags -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="{{ .Site.Title }}">
<meta name="msapplication-TileColor" content="{{ .Site.Params.tileColor | default "#2d89ef" }}">
<meta name="format-detection" content="telephone=no">
```

---

## 10. VERIFY CONFIG PARAMETERS

**File:** `config.toml`

**Verify these parameters exist in Params section. Add if missing:**

```toml
[params]
  twitter = "@yourTwitterHandle"
  authors = "Your Name"
  siteLogo = "https://demo.penyadap.com/logo.png"
  tileColor = "#2d89ef"
```

**Check these values in your config and update accordingly.**

---

## IMPLEMENTATION CHECKLIST

- [ ] Fix heading hierarchy (H1 to H2)
- [ ] Fix Twitter description logic
- [ ] Implement breadcrumb schema
- [ ] Add semantic HTML tags
- [ ] Update footer tag
- [ ] Enhance image rendering (add decoding, fallback alt)
- [ ] Add article publication meta tags
- [ ] Create custom robots.txt (optional)
- [ ] Add mobile app meta tags (optional)
- [ ] Verify config parameters
- [ ] Test with Google Structured Data Tool
- [ ] Submit to Google Search Console
- [ ] Monitor rankings in GSC

---

## VALIDATION STEPS

After implementing each change:

1. **Build Hugo:**
   ```bash
   hugo
   ```

2. **Check for errors in template:**
   ```bash
   hugo server --verbose
   ```

3. **Validate HTML:**
   - Open page in browser
   - Right-click → View Page Source
   - Look for changes

4. **Test Schema:**
   - Go to: https://validator.schema.org
   - Paste your page source
   - Should show no errors

5. **Test Meta Tags:**
   - Use: https://heymeta.com
   - Paste your page URL
   - Review all meta tags

---

## ROLLBACK INSTRUCTIONS

If you need to revert any change:

1. Keep original files backed up
2. Each change is isolated
3. Revert the specific section that caused issues
4. Rebuild Hugo

---

## FILES MODIFIED SUMMARY

| File | Changes | Priority |
|------|---------|----------|
| `themes/hugo_framework/layouts/_default/single.html` | Fix H1/H2, add semantic tags | CRITICAL |
| `themes/hugo_framework/layouts/partials/component/meta/data.html` | Fix Twitter logic, add article dates | HIGH |
| `themes/hugo_framework/layouts/partials/component/meta/schema/breadcrumbs.json` | Implement schema | HIGH |
| `themes/hugo_framework/layouts/partials/footer.html` | Add footer semantic tag | MEDIUM |
| `themes/hugo_framework/layouts/_default/_markup/render-image.html` | Add decoding, fallback alt | MEDIUM |
| `layouts/robots.txt` | Create custom robots | OPTIONAL |
| `config.toml` | Verify parameters | MEDIUM |

---

**Generated:** April 1, 2026  
**Reference:** SEO_ANALYSIS_REPORT.md
