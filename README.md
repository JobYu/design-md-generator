# design-md-generator

**Languages:** English (this page) · [繁體中文](./README.zh-Hant.md)

A **Cursor Agent Skill** that produces a full design-system package—aligned with the spirit of [Google Stitch DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/)—from your project context or a guided interview, including preview assets.

## What is DESIGN.md?

[DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/) is a **plain Markdown** design-system document: visual and interaction rules so AI coding agents or tools can build consistent UIs without Figma exports or an extra schema.


| File        | Read by              | Defines                          |
| ----------- | -------------------- | -------------------------------- |
| `AGENTS.md` | Coding agents        | How to build the project         |
| `DESIGN.md` | Design / coding agents | How the product should look and feel |


For curated examples, see **[Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md)**: real-site extracts you can copy, with `DESIGN.md` and `preview.html` / `preview-dark.html` templates.  
**This repo** focuses on **generating from scratch**: process and section templates in [`SKILL.md`](./SKILL.md)—for your own product when there is no ready-made `DESIGN.md` to start from.

## Contents of this repository


| File                     | Description                                                                                                                                      |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| [`SKILL.md`](./SKILL.md) | **design-md-generator**: triggers, autonomous vs guided modes, nine-chapter master template, mobile extensions, anti-pattern checklist, and the default **four-file** output under `design-system/`. |


The skill steers agents toward sections that match the [Stitch DESIGN.md format](https://stitch.withgoogle.com/docs/design-md/format/), with optional micro-interaction previews and light/dark HTML (details in `SKILL.md`).

## Usage

1. Install or reference this repo’s `SKILL.md` per Cursor [Agent Skills](https://docs.cursor.com) (path depends on your skills directory).
2. Use trigger phrases in chat, e.g. **“generate DESIGN.md”**, **“design system document”**, **“產品視覺規範”**, etc. (full list in the `triggers` field at the top of `SKILL.md`).
3. Choose **autonomous mode** (analyze README, styles, stack) or **guided mode** (step-by-step interview on product personality and constraints).
4. By default, get `DESIGN.md`, brand-facing `README.md`, `preview.html`, and `preview-dark.html` under `design-system/` in the target project (or another root you specify).

To lean toward an existing public `DESIGN.md`, pick a reference from the [awesome-design-md list](https://github.com/VoltAgent/awesome-design-md) and ask the agent to align or merge with your product needs.

## How this repo relates to awesome-design-md


|        | [awesome-design-md](https://github.com/VoltAgent/awesome-design-md) | **This project (design-md-generator)** |
| ------ | --------------------------------------------------------------------- | --------------------------------------- |
| Role   | Curated `DESIGN.md` + preview HTML from real sites                    | Agent workflow and templates to write a set from scratch |
| Best for | Quickly matching well-known product visuals                         | Own brand, interviews, and avoiding generic “AI slop” defaults |


Both aim for the same goal: a single, agent-readable source of truth anchored in **`DESIGN.md`**.

## Further reading

- [Stitch: DESIGN.md overview](https://stitch.withgoogle.com/docs/design-md/overview/)
- [Stitch: DESIGN.md format](https://stitch.withgoogle.com/docs/design-md/format/)
- [VoltAgent / Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md)
- [Custom DESIGN.md request (getdesign.md)](https://getdesign.md/request)

## License

This repository is licensed under the [MIT License](./LICENSE). When using community templates or third-party `DESIGN.md` files, follow each source’s terms.
