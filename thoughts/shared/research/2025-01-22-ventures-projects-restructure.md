---
date: 2025-01-22T12:00:00-05:00
researcher: Lucas Garcia de Viedma
git_commit: c8c21546003a0480c6e7ed0f96e356b288c97d9a
branch: master
repository: me
topic: "Ventures vs Projects Restructure with Tabs"
tags: [research, codebase, ventures, projects, tabs, ui-restructure]
status: complete
last_updated: 2025-01-22
last_updated_by: Lucas Garcia de Viedma
---

# Research: Ventures vs Projects Restructure with Tabs

**Date**: 2025-01-22
**Researcher**: Lucas Garcia de Viedma
**Git Commit**: c8c21546003a0480c6e7ed0f96e356b288c97d9a
**Branch**: master
**Repository**: me

## Research Question

How to separate ventures (businesses) from projects (products/services) and implement a tabbed interface for switching between them. Ventures should include CloudClerk, Orbital, and Numia. Projects should include Token Pulse, NumiaAI, Data Lenses, Celestia Data, NumiaSQL, and NumiaAPI. Convea should be replaced with Orbital (enterorbital.com).

## Summary

The codebase currently has a single "Ventures & Projects" section that displays 8 cards in a 3-column grid layout, plus a tech stack card. There is no existing tab component - a new tabbed interface will need to be created. The current items mix businesses (ventures) and products (projects) together without distinction.

## Current Structure

### Section Location
- **File**: [index.html:182-349](index.html#L182-L349)
- **Section ID**: `ventures`
- **Section Header**: "Ventures & Projects"

### Current Cards (8 total + tech stack)

| # | Name | Company Logo | Type (Proposed) | Lines |
|---|------|-------------|-----------------|-------|
| 1 | CloudClerk | cloudclerk_ai_logo.jfif | **Venture** | 188-201 |
| 2 | Token Pulse | numia.jfif | Project | 202-215 |
| 3 | NumiaAI | numia.jfif | Project | 216-229 |
| 4 | Data Lenses | numia.jfif | Project | 230-243 |
| 5 | Celestia Data | numia.jfif | Project | 244-257 |
| 6 | NumiaSQL | numia.jfif | Project | 258-271 |
| 7 | NumiaAPI | numia.jfif | Project | 272-285 |
| 8 | Convea | convea_ai_logo.jfif | **Replace with Orbital** | 286-299 |
| 9 | Tech Stack | N/A | Keep in both tabs or separate | 300-347 |

### Navigation Link
- [index.html:74](index.html#L74) - Nav link points to `#ventures`

### Hero Section Cards
The hero section (lines 109-177) has employment cards that also need updating if Convea is replaced:
- [index.html:127-143](index.html#L127-L143) - Convea hero card needs to become Orbital

## CSS Structure

### Relevant CSS Classes in [styles.css](styles.css)
- `.ventures` (line 359) - Main section container
- `.ventures-grid` (line 364) - 3-column grid layout
- `.venture-card` (line 372) - Individual card styling
- `.venture-image` (line 386) - Card image container
- `.venture-company-logo` (line 393) - Company logo overlay
- `.venture-content` (line 423) - Card content area
- `.venture-badge` (line 428) - Status badge styling
- `.venture-title-link` (line 455) - Title link styling
- `.venture-read-more` (line 473) - Read more link styling
- `.venture-card-techstack` (line 488) - Tech stack card variant

### No Existing Tab Components
The codebase does not have any existing tab components. A new tab system will need to be created.

## Proposed New Structure

### Ventures Tab (Businesses)
1. **CloudClerk** - BigQuery cost monitoring (existing)
2. **Numia** - NEW card needed for the Numia business
3. **Orbital** - Replace Convea, link to enterorbital.com

### Projects Tab (Products/Services)
1. Token Pulse (existing, Numia project)
2. NumiaAI (existing, Numia project)
3. Data Lenses (existing, Numia project)
4. Celestia Data (existing, Numia project)
5. NumiaSQL (existing, Numia project)
6. NumiaAPI (existing, Numia project)

### Tech Stack Card
Decision needed: Keep in Projects tab, Ventures tab, or show in both

## Files Requiring Modification

### index.html
1. Update section header to add tab navigation
2. Reorganize cards into two groups (ventures/projects)
3. Replace Convea card (lines 286-299) with Orbital
4. Add new Numia venture card
5. Update hero section Convea card (lines 127-143) to Orbital
6. Add JavaScript for tab switching

### styles.css
1. Add tab navigation styles
2. Add tab content visibility styles
3. Add active/inactive tab state styles

### Assets Needed
1. Orbital logo image (for employment/ folder)
2. Orbital project screenshot (for projects/ folder)
3. Numia venture screenshot (for projects/ folder)

## Code References

- Main ventures section: `index.html:182-349`
- Convea card to replace: `index.html:286-299`
- Hero Convea card to replace: `index.html:127-143`
- CSS ventures styles: `styles.css:358-573`
- Grid responsive breakpoints: `styles.css:1136-1138`, `styles.css:1207-1209`

## Architecture Documentation

### Current Card HTML Structure
```html
<div class="venture-card">
    <div class="venture-image">
        <img src="projects/[image].png" alt="[Name]" class="venture-project-img">
    </div>
    <div class="venture-content">
        <div class="venture-company-logo">
            <img src="employment/[logo].jfif" alt="[Company]">
        </div>
        <div class="venture-badge">Active</div>
        <h3><a href="[url]" target="_blank" class="venture-title-link">[Name] [svg icon]</a></h3>
        <p>[Description]</p>
        <a href="[detail-page]" class="venture-read-more">Read more</a>
    </div>
</div>
```

### Proposed Tab Structure
```html
<section id="ventures" class="ventures">
    <div class="section-header">
        <h2>Ventures & Projects</h2>
        <div class="tab-navigation">
            <button class="tab-btn active" data-tab="ventures">Ventures</button>
            <button class="tab-btn" data-tab="projects">Projects</button>
        </div>
    </div>
    <div class="tab-content" id="ventures-content">
        <div class="ventures-grid">
            <!-- CloudClerk, Numia, Orbital cards -->
        </div>
    </div>
    <div class="tab-content hidden" id="projects-content">
        <div class="ventures-grid">
            <!-- Token Pulse, NumiaAI, Data Lenses, etc. -->
            <!-- Tech Stack card -->
        </div>
    </div>
</section>
```

## Open Questions

1. Should Orbital card link to enterorbital.com or a project detail page?
2. What screenshot/image should be used for the Orbital venture card?
3. What logo image should be used for Orbital?
4. What description should the Numia venture card have?
5. What screenshot should be used for the Numia venture card?
6. Should Tech Stack card appear in both tabs or only Projects?
7. Should the hero section's Convea card also be updated to Orbital?
