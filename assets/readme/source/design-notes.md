# README illustration source

Audience: authors and makers who need consistent editorial illustrations.
Value: turn a topic into a conceptual paper-collage illustration with a fixed visual language.
Proof: three actual outputs approved by the repository owner.
First action: invoke $shuai-illustration-gen with a topic.
Theme: warm ivory, ink black, paper white, warm gray, vermilion; editorial typography and paper specimens.

The PNG layers are existing outputs, reused without new image generation. The SVG controls layout and typography. These are README presentation assets only; SKILL.md does not load or depend on them.

Render from this directory:

```bash
rsvg-convert --width 1800 --height 1170 hero-layout.svg --output ../hero.png
```
