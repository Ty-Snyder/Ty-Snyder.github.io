# Ty Snyder Robotics — personal portfolio site

Static HTML site, no build step. Deployed to GitHub Pages by `.github/workflows/static.yml` on every push to `main` (uploads the whole repo).

## Stack
- Bootstrap 5.3.0 (CSS + bundle JS via jsDelivr), Font Awesome 6.0.0 (cdnjs). MathJax 3 only on `projects/quadruped_V1.html`.
- One shared stylesheet: `style.css`. Pages in subfolders link it as `../style.css`.

## Layout
- `index.html` — home: hero (headshot, badges), Skills (4 boxes), Featured Projects (3 cards), Research & Professional Experience (3 cards), Core Principles, Combat Robotics (dark section, 2 bot links), Earlier Work (compact cards for high school projects, e.g. VEX 2112A), footer.
- `resume.html` — embeds `assets/TySnyder_resume.pdf` in an `<object class="pdf-viewer">`.
- `projects/` — `gps-rc-car.html`, `Revit_Addon.html`, `quadruped_V1.html`, `digital-guitar.html` (in progress; `<!-- TODO -->` comments and `.img-placeholder` boxes mark unfinished text/photos); assets in `projects/assets/{images,videos}` plus PDFs.
- `combat-robots/` — `Malware.html` (30lb), `Executioner.html` (15lb); images in `combat-robots/assets/images/`.

## Conventions
- Navbar and footer are copy-pasted into all 7 pages (no includes). Any nav/footer change must be applied to every page, with paths adjusted (`../` in subfolders, sibling-relative within the same folder).
- Active page marking: `nav-link active` + `aria-current="page"` for top-level pages; on subpages mark both the dropdown toggle and the `dropdown-item` as `active`.
- Project/bot page template: `header.project-hero` with inline-style gradient + background image → `main.container` with overview (`col-md-8`) and spec card/table (`col-md-4`) → "Sub Sections" of alternating image/text rows (`flex-md-row-reverse` on every other row) → media (video / YouTube iframe / Bootstrap carousel / PDF) → footer.
- Adding a project means: new page, add to the Projects (or Combat Robotics) dropdown on all pages, and add a card on `index.html`.
- Footer social links carry `aria-label`; external links use `target="_blank" rel="noopener noreferrer"`.

## Known rough edges
- Several large unoptimized media files (e.g. `projects/assets/videos/RCCar.mp4` ~50MB, `MalwareAir.jpeg` ~16MB, `Malware.jpeg` ~11MB).
- Some filenames contain spaces (`Pit Image.jpg`, `Team Photo.jpg`, `Quadruped CAD.png`, `RC Wiring.pdf`).
- Hero sections use inline `style` for background/padding rather than CSS classes.
- Files use CRLF line endings (git `core.autocrlf=true`).
