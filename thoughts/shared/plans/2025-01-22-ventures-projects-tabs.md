# Ventures & Projects Tab Restructure Implementation Plan

## Overview

Restructure the "Ventures & Projects" section into a tabbed interface that separates businesses (Ventures) from products/services (Projects). Replace Convea with Orbital throughout the site.

## Current State Analysis

- Single "Ventures & Projects" section displaying 8 cards + tech stack in a 3-column grid
- No tab component exists - needs to be created
- Convea card and hero card need to be replaced with Orbital
- Missing Numia venture card (only has Numia projects)

### Key Discoveries:
- Main section: `index.html:182-349`
- Hero Convea card: `index.html:127-143`
- CSS styles: `styles.css:358-573`
- No existing tab components in codebase

## Desired End State

**Ventures Tab (3 cards):**
1. CloudClerk - BigQuery cost monitoring
2. Numia - Blockchain data cloud platform
3. Orbital - AI agents venture studio

**Projects Tab (6 cards + tech stack):**
1. Token Pulse
2. NumiaAI
3. Data Lenses
4. Celestia Data
5. NumiaSQL
6. NumiaAPI
7. Tech Stack card

**Hero Section:**
- Orbital replaces Convea

### Verification:
- Tab switching works smoothly
- All cards display correctly in their respective tabs
- Hero section shows Orbital instead of Convea
- Responsive design maintained

## What We're NOT Doing

- Creating separate detail pages for Numia or Orbital ventures
- Modifying existing project detail pages
- Changing the overall site design/color scheme
- Adding animations beyond simple tab transitions

## Implementation Approach

Use vanilla CSS and JavaScript for the tab component to maintain the site's simplicity. Reorganize existing cards and add two new venture cards (Numia, Orbital).

---

## Phase 1: Add Tab CSS Styles

### Overview
Add CSS classes for tab navigation and content visibility.

### Changes Required:

**File**: `styles.css`
**Location**: After `.section-desc` styles (around line 357)

```css
/* Tab Navigation */
.tab-navigation {
    display: flex;
    justify-content: center;
    gap: 0.5rem;
    margin-top: 1.5rem;
}

.tab-btn {
    padding: 0.75rem 1.5rem;
    font-size: 14px;
    font-weight: 500;
    color: var(--color-text-muted);
    background: transparent;
    border: 1px solid var(--color-border);
    border-radius: 100px;
    cursor: pointer;
    transition: all var(--transition);
}

.tab-btn:hover {
    color: var(--color-text);
    border-color: var(--color-text-muted);
}

.tab-btn.active {
    color: var(--color-text);
    background: var(--color-surface);
    border-color: var(--color-text);
}

/* Tab Content */
.tab-content {
    display: block;
}

.tab-content.hidden {
    display: none;
}
```

### Success Criteria:

#### Automated Verification:
- [x] CSS file is valid (no syntax errors)
- [x] Page loads without console errors

#### Manual Verification:
- [ ] Tab button styles appear correctly when HTML is added

---

## Phase 2: Restructure HTML with Tab Navigation

### Overview
Add tab navigation buttons and reorganize cards into two tab content containers.

### Changes Required:

**File**: `index.html`
**Location**: Lines 182-349 (ventures section)

Replace the entire ventures section with:

```html
<section id="ventures" class="ventures">
    <div class="section-header">
        <h2>Ventures & Projects</h2>
        <p class="section-desc">Businesses I've built and products I've shipped</p>
        <div class="tab-navigation">
            <button class="tab-btn active" data-tab="ventures">Ventures</button>
            <button class="tab-btn" data-tab="projects">Projects</button>
        </div>
    </div>

    <!-- Ventures Tab -->
    <div class="tab-content" id="ventures-tab">
        <div class="ventures-grid">
            <!-- CloudClerk -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/cloudclerk.png" alt="CloudClerk" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/cloudclerk_ai_logo.jfif" alt="CloudClerk">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://www.cloudclerk.ai/" target="_blank" class="venture-title-link">CloudClerk <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>BigQuery cost monitoring and optimization platform. We leverage over 5 years of experience of big data processing in BigQuery to help teams reduce costs through proper observability tools plus the usage of AI Agents.</p>
                    <a href="projects/cloudclerk.html" class="venture-read-more">Read more →</a>
                </div>
            </div>
            <!-- Numia -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/numiabanner.png" alt="Numia" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/numia.jfif" alt="Numia">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://numia.xyz/" target="_blank" class="venture-title-link">Numia <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>The first data cloud platform for blockchains. A single place where institutions, foundations, and developers can access blockchain infrastructure, processing, analytics, and business intelligence.</p>
                    <a href="https://numia.xyz/" target="_blank" class="venture-read-more">Learn more →</a>
                </div>
            </div>
            <!-- Orbital -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/orbitalbanner.png" alt="Orbital" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="orbital.svg" alt="Orbital">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://enterorbital.com/" target="_blank" class="venture-title-link">Orbital <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>Venture studio exploring AI agents within complex systems. Consulting, research, and insights on implementing intelligent automation. The engineering foundation behind CloudClerk, Numia, and more.</p>
                    <a href="https://enterorbital.com/" target="_blank" class="venture-read-more">Learn more →</a>
                </div>
            </div>
        </div>
    </div>

    <!-- Projects Tab -->
    <div class="tab-content hidden" id="projects-tab">
        <div class="ventures-grid">
            <!-- Token Pulse -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/pulse.png" alt="Token Pulse" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/numia.jfif" alt="Numia">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://tokenpulse.numia.xyz/" target="_blank" class="venture-title-link">Token Pulse <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>Real time analytics dashboard that allows blockchain foundation teams to track different health and usage KPIs of their governance tokens. Currently used by the DYDX, Celestia and Cosmoshub foundation teams.</p>
                    <a href="projects/tokenpulse.html" class="venture-read-more">Read more →</a>
                </div>
            </div>
            <!-- NumiaAI -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/nuamiai.jfif" alt="NumiaAI" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/numia.jfif" alt="Numia">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://chat.numia.xyz/" target="_blank" class="venture-title-link">NumiaAI <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>Domain expert chatbot developed to provide support for the trading, reporting and strategy teams of blockchain foundations. Currently used by the DYDX foundation.</p>
                    <a href="projects/numiaai.html" class="venture-read-more">Read more →</a>
                </div>
            </div>
            <!-- Data Lenses -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/lenses.jfif" alt="Data Lenses" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/numia.jfif" alt="Numia">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://www.datalenses.zone/" target="_blank" class="venture-title-link">Data Lenses <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>Analytics dashboard aimed towards showcasing specific blockchain tailored metrics the blockchain foundations want to share with their users. Currently used by the DYDX, Cosmoshub and Osmosis teams.</p>
                    <a href="projects/datalenses.html" class="venture-read-more">Read more →</a>
                </div>
            </div>
            <!-- Celestia Data -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/celestia.jfif" alt="Celestia Data" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/numia.jfif" alt="Numia">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://celestiadata.com/" target="_blank" class="venture-title-link">Celestia Data <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>Analytics dashboard aimed towards showcasing specific blockchain tailored metrics the blockchain foundations want to share with their users. Designed only for the Celestia foundation.</p>
                    <a href="projects/celestiadata.html" class="venture-read-more">Read more →</a>
                </div>
            </div>
            <!-- NumiaSQL -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/numiasql.png" alt="NumiaSQL" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/numia.jfif" alt="Numia">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://docs.numia.xyz/sql/overview/whats-numia-sql/" target="_blank" class="venture-title-link">NumiaSQL <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>Ingestion, processing and maintenance of over 50TB of blockchain data about the Cosmos ecosystem (+50 chains) for public access. In addition, curated datasets for private use for blockchain foundations that require it.</p>
                    <a href="https://docs.numia.xyz/sql/overview/whats-numia-sql/" target="_blank" class="venture-read-more">Read more →</a>
                </div>
            </div>
            <!-- NumiaAPI -->
            <div class="venture-card">
                <div class="venture-image">
                    <img src="projects/apis.jfif" alt="NumiaAPI" class="venture-project-img">
                </div>
                <div class="venture-content">
                    <div class="venture-company-logo">
                        <img src="employment/numia.jfif" alt="Numia">
                    </div>
                    <div class="venture-badge">Active</div>
                    <h3><a href="https://docs.numia.xyz/api/overview/whats-numia-api/" target="_blank" class="venture-title-link">NumiaAPI <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/></svg></a></h3>
                    <p>Extensive set of public and private endpoints that power frontends or large blockchain players like Osmosis, Neutron, Xion, and chain specific pages for Defillama, DexScreener, Coingecko or Coinmarketcap.</p>
                    <a href="https://docs.numia.xyz/api/overview/whats-numia-api/" target="_blank" class="venture-read-more">Read more →</a>
                </div>
            </div>
            <!-- Tech Stack Card -->
            <div class="venture-card venture-card-techstack">
                <div class="venture-content">
                    <div class="venture-badge">Tech Stack</div>
                    <h3>Tools & Technologies</h3>
                    <p>The technologies I've used day to day to build these data products and scale them.</p>
                    <div class="techstack-carousels">
                        <div class="techstack-row">
                            <div class="techstack-track">
                                <span class="techstack-item"><img src="stack/bq.png" alt="">BigQuery</span>
                                <span class="techstack-item"><img src="stack/ch.png" alt="">ClickHouse</span>
                                <span class="techstack-item"><img src="stack/psql.png" alt="">PostgreSQL</span>
                                <span class="techstack-item"><img src="stack/mongo.svg" alt="">MongoDB</span>
                                <span class="techstack-item"><img src="stack/tb.png" alt="">TinyBird</span>
                                <span class="techstack-item"><img src="stack/bq.png" alt="">BigQuery</span>
                                <span class="techstack-item"><img src="stack/ch.png" alt="">ClickHouse</span>
                                <span class="techstack-item"><img src="stack/psql.png" alt="">PostgreSQL</span>
                                <span class="techstack-item"><img src="stack/mongo.svg" alt="">MongoDB</span>
                                <span class="techstack-item"><img src="stack/tb.png" alt="">TinyBird</span>
                            </div>
                        </div>
                        <div class="techstack-row">
                            <div class="techstack-track techstack-track-reverse">
                                <span class="techstack-item"><img src="stack/dbt.png" alt="">DBT (Core & Cloud)</span>
                                <span class="techstack-item"><img src="stack/gcp.png" alt="">GCP</span>
                                <span class="techstack-item"><img src="stack/looker.png" alt="">Looker</span>
                                <span class="techstack-item"><img src="stack/dbt.png" alt="">DBT (Core & Cloud)</span>
                                <span class="techstack-item"><img src="stack/gcp.png" alt="">GCP</span>
                                <span class="techstack-item"><img src="stack/looker.png" alt="">Looker</span>
                                <span class="techstack-item"><img src="stack/dbt.png" alt="">DBT (Core & Cloud)</span>
                                <span class="techstack-item"><img src="stack/gcp.png" alt="">GCP</span>
                                <span class="techstack-item"><img src="stack/looker.png" alt="">Looker</span>
                            </div>
                        </div>
                        <div class="techstack-row">
                            <div class="techstack-track">
                                <span class="techstack-item"><img src="stack/python.jfif" alt="">Python</span>
                                <span class="techstack-item"><img src="stack/ts.png" alt="">TypeScript</span>
                                <span class="techstack-item"><img src="stack/nexjs.png" alt="">Next.js</span>
                                <span class="techstack-item"><img src="stack/react.png" alt="">React</span>
                                <span class="techstack-item"><img src="stack/python.jfif" alt="">Python</span>
                                <span class="techstack-item"><img src="stack/ts.png" alt="">TypeScript</span>
                                <span class="techstack-item"><img src="stack/nexjs.png" alt="">Next.js</span>
                                <span class="techstack-item"><img src="stack/react.png" alt="">React</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
```

### Success Criteria:

#### Automated Verification:
- [x] HTML is valid (no unclosed tags)
- [x] Page loads without console errors

#### Manual Verification:
- [ ] Ventures tab shows 3 cards (CloudClerk, Numia, Orbital)
- [ ] Projects tab shows 6 cards + tech stack
- [ ] All images load correctly
- [ ] All links work

---

## Phase 3: Add Tab JavaScript

### Overview
Add JavaScript to handle tab switching functionality.

### Changes Required:

**File**: `index.html`
**Location**: Before closing `</body>` tag

```html
<script>
    document.querySelectorAll('.tab-btn').forEach(button => {
        button.addEventListener('click', () => {
            // Update active button
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
            button.classList.add('active');

            // Show/hide tab content
            const tabName = button.dataset.tab;
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.add('hidden');
            });
            document.getElementById(tabName + '-tab').classList.remove('hidden');
        });
    });
</script>
```

### Success Criteria:

#### Automated Verification:
- [x] No JavaScript syntax errors in console

#### Manual Verification:
- [ ] Clicking "Ventures" tab shows ventures content
- [ ] Clicking "Projects" tab shows projects content
- [ ] Active tab button is visually highlighted
- [ ] Tab switching is smooth

---

## Phase 4: Update Hero Section

### Overview
Replace Convea hero card with Orbital.

### Changes Required:

**File**: `index.html`
**Location**: Lines 127-143 (Convea hero card)

Replace:
```html
<a href="#journey" class="hero-card">
    <div class="hero-card-logo">
        <img src="employment/convea_ai_logo.jfif" alt="Convea Logo">
    </div>
    <div class="hero-card-info">
        <h3>Founding Team - Data Lead</h3>
        <span>Convea</span>
    </div>
    <ul class="hero-card-points">
        <li>Ecommerce</li>
        <li>AI Agents</li>
        <li>ClickHouse</li>
    </ul>
    <div class="hero-card-arrow">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
    </div>
</a>
```

With:
```html
<a href="#journey" class="hero-card">
    <div class="hero-card-logo">
        <img src="orbital.svg" alt="Orbital Logo">
    </div>
    <div class="hero-card-info">
        <h3>Cofounder</h3>
        <span>Orbital</span>
    </div>
    <ul class="hero-card-points">
        <li>AI Agents</li>
        <li>Consulting</li>
        <li>Venture Studio</li>
    </ul>
    <div class="hero-card-arrow">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
    </div>
</a>
```

### Success Criteria:

#### Automated Verification:
- [x] HTML is valid
- [x] Page loads without errors

#### Manual Verification:
- [ ] Orbital logo displays correctly in hero section
- [ ] Hero card information is accurate

---

## Phase 5: Update Journey Section

### Overview
Replace Convea entry with Orbital in the professional journey timeline.

### Changes Required:

**File**: `index.html`
**Location**: Lines 425-432 (Convea timeline entry)

Replace:
```html
<div class="timeline-item">
    <div class="timeline-date">2025 - Present</div>
    <div class="timeline-content">
        <h3>Founding Team - Data Lead</h3>
        <span class="timeline-company">Convea</span>
        <p>eCommerce analytics platform bringing together sales, marketing, and advertising data. Building AI-driven insights with ClickHouse as the backbone.</p>
    </div>
</div>
```

With:
```html
<div class="timeline-item">
    <div class="timeline-date">2025 - Present</div>
    <div class="timeline-content">
        <h3>Cofounder</h3>
        <span class="timeline-company">Orbital</span>
        <p>Venture studio exploring AI agents within complex systems. Consulting, research, and insights on implementing intelligent automation.</p>
    </div>
</div>
```

### Success Criteria:

#### Automated Verification:
- [x] HTML is valid

#### Manual Verification:
- [ ] Journey section shows Orbital instead of Convea
- [ ] Timeline order is correct

---

## Testing Strategy

### Manual Testing Steps:

1. Open the page in a browser
2. Verify Ventures tab is active by default and shows 3 cards
3. Click Projects tab - verify 6 cards + tech stack appear
4. Click Ventures tab - verify it switches back
5. Scroll to hero section - verify Orbital card displays
6. Scroll to journey section - verify Orbital timeline entry
7. Test on mobile viewport - verify responsive design
8. Click all external links - verify they open correctly

## References

- Research document: `thoughts/shared/research/2025-01-22-ventures-projects-restructure.md`
- Main section: `index.html:182-349`
- Hero section: `index.html:109-177`
- Journey section: `index.html:412-458`
- CSS styles: `styles.css:358-573`
