# Al Zorah — Blog / Insights

A production-ready, self-contained blog for Al Zorah — a listing page plus nine
article pages — matched to the theme, colours, fonts and chrome of **alzorahcity.com**.
`index.html` is the root/home so it deploys correctly on any static host (Vercel,
GitHub Pages, Netlify).

| File | Purpose |
|------|---------|
| `index.html` | Main blog **listing** page — hero, category filter, featured post, 9-article grid, register-interest CTA |
| `blog-villas.html` | Article — Villas for Sale in Ajman (Content-Plan brief #1) — also the **canonical template** all articles mirror |
| `blog-apartments.html` | Article — Apartments for Sale in Ajman (brief #2) |
| `blog-beachfront-villas.html` | Article — Beachfront Villas in Ajman (brief #3) |
| `blog-waterfront-apartments.html` | Article — Waterfront Apartments, Creekside & Marina (brief #4) |
| `blog-off-plan.html` | Article — Off-Plan Property in Ajman 2026 (brief #5) |
| `blog-3-bedroom-villas.html` | Article — 3-Bedroom Villas in Ajman (brief #6) |
| `blog-invest-ajman.html` | Article — Why Invest in Ajman 2026, ROI & outlook (brief #7) |
| `blog-ajman-vs-dubai.html` | Article — Ajman vs Dubai, price/yield/lifestyle (brief #8) |
| `blog-freehold.html` | Article — Freehold Property in Ajman for foreign buyers (brief #9) |
| `assets/css/blog.css` | Full design system (tokens + components) |
| `assets/js/blog.js` | Sticky header, mobile nav, category filter, FAQ accordion, scroll-reveal, TOC scrollspy |
| `assets/fonts/` | The three brand fonts pulled from the live site |
| `assets/img/` | Brand logo, social icons + article imagery (from the live site's storage) |

## Design tokens (from alzorahcity.com)

```
Ink / chrome     #07171D      Dark surfaces  #212531 / #2f3441
Body copy        #606060      Hairlines      #e4e4e4 / #f1f1f1
Muted labels     #808080      Off-white band #f7f6f3
Gold accent      #d69915  (used sparingly — eyebrows, links, table headers)

Display font     Monotype-Regular   (hero + article headings)
Body font        ScalaSans-Light    (all body copy)
Label font       ChongModern        (eyebrows, nav, footer, small caps)
```

The site uses **dark chrome** (deep-ink header + footer) around a white content
area, so the white brand logo works in every context.

## The 9 articles

All nine outlines from `Copy_of_AlZorah_12Month_Content_Plan_.xlsx` are built as full
article pages (listed above) and linked from the listing grid. Every page follows its
sheet brief section-by-section — intro, all H2s, comparison tables/key-facts where the
brief calls for them, and the exact FAQ questions — and reuses the same header, footer,
CTA band and sidebar chrome as `blog-villas.html`.

> **Content note:** the plan repeatedly warns *do not invent pricing, sqft or unit
> mix*. The article copy honours this — figures are framed as **"starting from"** and
> routed to the sales team, with a visible disclosure note. Swap in confirmed data
> when sales provides it.

## Preview locally

Because the pages load fonts/images by relative path, open them through a server
(not `file://`):

```bash
cd "D:\Code Files\al-zohra"
python -m http.server 8000
# then visit http://localhost:8000/index.html
```

## Integrating into the Laravel site

The markup is framework-free HTML. To port into the existing site: move the article
body into your Blade layout, keep `assets/css/blog.css` + `assets/js/blog.js`, and
point nav/footer links at real routes (they currently use absolute alzorahcity.com
URLs). The listing grid and article body are the two blocks to make dynamic.
