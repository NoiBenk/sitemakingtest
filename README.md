# 🎨 Noi's Web Zone - Templating System

## 📁 File Structure

```
your-website/
├── template.html          ← The reusable template (navbar, sidebar, chrome)
├── template-loader.js     ← Script that loads the template
├── style.css              ← Styles for the template
├── style-additions.css    ← Styles for page content
├── index.html             ← Homepage (just content!)
├── blog.html              ← Blog page (just content!)
├── video.html             ← Videos page (just content!)
└── ... (your other pages)
```

## 🚀 How It Works

### The Magic
Instead of copying the navbar, sidebar, and window chrome to every page, you now:
1. **Create minimal HTML pages** with just your content
2. **The template-loader.js script** automatically wraps your content in the full template
3. **Change the navbar once** in `template.html` → updates everywhere! ✨

### Creating a New Page

**Before (the old way):**
```html
<!DOCTYPE html>
<html>
  <head>...</head>
  <body>
    <!-- Title bar -->
    <div class="titlebar">...</div>
    <!-- Menu bar -->
    <div class="menubar">...</div>
    <!-- Nav toolbar -->
    <div class="navbar">...</div>
    <!-- Address bar -->
    <div class="addressbar">...</div>
    <!-- Sidebar -->
    <div class="left-col">...</div>
    
    <!-- YOUR ACTUAL CONTENT (finally!) -->
    <div class="right-col">
      <h1>My Page Content</h1>
      <p>Stuff here...</p>
    </div>
    
    <!-- Status bar -->
    <div class="statusbar">...</div>
  </body>
</html>
```

**After (the new way):**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <script src="template-loader.js" 
          data-title="Noi's Site — My Page" 
          data-subtitle="My Page" 
          data-address="http://noi.webzone/mypage.html"
          data-nav="mypage"></script>
</head>
<body>

<div id="page-content">
  <h1>My Page Content</h1>
  <p>Stuff here...</p>
</div>

</body>
</html>
```

**That's it!** The script automatically loads everything else.

## 🛠️ Template Configuration

When including the `template-loader.js` script, you can configure:

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `data-title` | Browser tab title | `"Noi's Site — Blog"` |
| `data-subtitle` | Shown in titlebar after "Noi's Web Zone —" | `"Blog"` |
| `data-address` | Shown in address bar | `"http://noi.webzone/blog.html"` |
| `data-nav` | Which nav item to highlight | `"blog"` (matches data-nav in template.html) |

## ✏️ Making Changes

### Want to add a new navbar button?
**Edit only:** `template.html`

Find the navbar section:
```html
<div class="navbar">
  <a href="index.html" data-nav="home">🏠 Home</a>
  <div class="nav-sep"></div>
  <a href="blog.html" data-nav="blog">📝 Blog</a>
  <!-- Add your new button here! -->
  <div class="nav-sep"></div>
  <a href="mynewpage.html" data-nav="mynewpage">🎨 New Page</a>
</div>
```

Don't forget to also add it to the sidebar pages list!

### Want to change the profile picture?
**Edit only:** `template.html`

Search for `litten-profile.png` and update the URL in the sidebar profile card.

### Want to add styles to a specific page?
**Edit:** `style-additions.css`

Add your page-specific CSS there to keep it organized!

### Want to change the overall XP theme styling?
**Edit:** `style.css`

All the window chrome, buttons, borders, and XP styling lives here.

## 🎯 Tips

1. **Always wrap your content in `<div id="page-content">`** - this is where the template injects it
2. **Scripts in your content will run automatically** after the template loads
3. **Use the `templateLoaded` event** if you need to wait:
   ```javascript
   window.addEventListener('templateLoaded', function() {
     // Your code here runs after template is loaded
   });
   ```
4. **The template includes all your CSS files** - no need to add `<link>` tags to individual pages

## 📝 Example: Creating a Contact Page

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <script src="template-loader.js" 
          data-title="Noi's Site — Contact" 
          data-subtitle="Contact" 
          data-address="http://noi.webzone/contact.html"
          data-nav="contact"></script>
</head>
<body>

<div id="page-content">
  <h2 style="color: var(--xp-blue-dark); margin-bottom: 10px;">📧 Contact Me</h2>
  
  <p style="font-size: 12px; line-height: 1.6;">
    Want to get in touch? Here's how:
  </p>

  <div class="info-tile" style="margin-top: 10px;">
    <div class="info-tile-label">📧 Email</div>
    <div class="info-tile-value">
      <a href="mailto:noi@example.com">noi@example.com</a>
    </div>
  </div>
</div>

</body>
</html>
```

**Done!** That's a complete page with navbar, sidebar, and everything.

## 🐛 Troubleshooting

**Problem:** "Template Loading Error"
- **Solution:** Make sure `template.html` is in the same folder as your page

**Problem:** Content doesn't show up
- **Solution:** Check that your content is wrapped in `<div id="page-content">`

**Problem:** Scripts don't run
- **Solution:** Use the `templateLoaded` event to wait for template to load first

**Problem:** Nav button not highlighting
- **Solution:** Make sure `data-nav` attribute matches between your page and template.html

## 🎉 Benefits

- ✅ **No more copy-paste** of navbar/sidebar to every page
- ✅ **Update once, change everywhere**
- ✅ **Cleaner, easier to read page files**
- ✅ **Better organization** with separate style files
- ✅ **Faster development** - focus on content, not chrome

---

Now go build something awesome! 🚀
