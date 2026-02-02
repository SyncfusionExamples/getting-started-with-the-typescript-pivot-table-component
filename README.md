# Getting Started — TypeScript Pivot Table Component (Syncfusion EJ2)

[![License](https://img.shields.io/badge/license-SEE%20LICENSE%20IN%20license-blue.svg)](license)
[![Last Updated](https://img.shields.io/github/last-commit/SyncfusionExamples/getting-started-with-the-typescript-pivot-table-component.svg)](https://github.com/SyncfusionExamples/getting-started-with-the-typescript-pivot-table-component/commits)
[![Languages](https://img.shields.io/github/languages/top/SyncfusionExamples/getting-started-with-the-typescript-pivot-table-component.svg)](https://github.com/SyncfusionExamples/getting-started-with-the-typescript-pivot-table-component)

> TypeScript quick-start demonstrating Syncfusion EJ2 `PivotView` (Pivot Table) with `FieldList`, `GroupingBar`, and `CalculatedField` — includes sample data, build scripts, and usage examples.

> **Demo (official):** https://ej2.syncfusion.com/demos/#/fluent2/pivot-table/overview.html

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Quick Start](#quick-start)
- [Minimal Example](#minimal-example)
- [Project Structure](#project-structure)
- [Configuration & Customization](#configuration--customization)
- [Development & Tests](#development--tests)
- [Contributing](#contributing)
- [License & Support](#license--support)

---

## Overview

This repository is a focused quick-start template that demonstrates how to integrate Syncfusion's `PivotView` (Pivot Table) into a TypeScript application. It highlights features such as `FieldList`, `GroupingBar` and `CalculatedField` and provides copy-paste-ready examples and build scripts using Webpack and TypeScript.

## Features

- Demo integration of `PivotView` with `FieldList` and `CalculatedField`.
- Sample dataset for immediate experimentation.
- Webpack + TypeScript build and dev server.
- Example of `PivotView.Inject(...)` usage to load optional modules.
- Small, focused codebase intended for learning and prototyping.

## Quick Start

Requirements:

- Node.js (LTS recommended)
- npm (or yarn)

Commands:

```bash
git clone https://github.com/SyncfusionExamples/getting-started-with-the-typescript-pivot-table-component.git
cd getting-started-with-the-typescript-pivot-table-component
npm install
npm start
```

Build for production:

```bash
npm run build
```

Note: this repo currently uses the umbrella package `@syncfusion/ej2` in `package.json`. For smaller bundles in production prefer installing the specific package:

```bash
npm install @syncfusion/ej2-pivotview
```

## Minimal Example

Core initialization (from `src/app/app.ts`):

```ts
import { PivotView, IDataSet, CalculatedField, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource';

PivotView.Inject(CalculatedField, FieldList);

const pivot: PivotView = new PivotView({
	dataSourceSettings: {
		dataSource: pivotData as IDataSet[],
		rows: [{ name: 'Country' }, { name: 'State' }],
		columns: [{ name: 'Date', caption: 'Date' }, { name: 'Product' }],
		values: [{ name: 'Amount', caption: 'Sold Amount' }, { name: 'Quantity', caption: 'Quantity' }],
		calculatedFieldSettings: [{ name: 'Total', formula: '"Sum(Amount)"+"Sum(Quantity)"' }]
	},
	showFieldList: true,
	allowCalculatedField: true,
	height: 350
});

pivot.appendTo('#PivotTable');
```

Sample data (`src/app/datasource.ts`):

```ts
export const pivotData = [
	{ Amount: 2100, Country: "Canada", Date: "FY 2005", Product: "Bike", Quantity: 22, State: "Alberta" },
	{ Amount: 1100, Country: "Canada", Date: "FY 2006", Product: "Van", Quantity: 32, State: "Quebec" },
	{ Amount: 3100, Country: "Canada", Date: "FY 2007", Product: "Car", Quantity: 22, State: "Alberta" }
];
```

Ensure an HTML mount point exists in `src/index.html`:

```html
<div id="PivotTable"></div>
```

## Project Structure

- `package.json` — scripts & deps
- `webpack.config.js` — bundler config
- `tsconfig.json` — TypeScript config
- `src/` — source files
	- `index.html` — demo host
	- `app/app.ts` — PivotView init
	- `app/datasource.ts` — sample data
	- `resources/styles/` — CSS
- `e2e/` — end-to-end test scaffolding

## Configuration & Customization

- To reduce bundle size, install only `@syncfusion/ej2-pivotview` and remove the umbrella `@syncfusion/ej2`.
- For large datasets enable `enableVirtualization` or use `DataManager`.
- Swap themes by importing the appropriate Syncfusion CSS for your chosen theme.

## Development & Tests

- Start dev server: `npm start` (webpack-dev-server)
- Build: `npm run build`
- E2E serve: `npm run serve`
- Run e2e tests: `npm test`

## Contributing

Contributions are welcome. Please follow these simple steps:

1. Fork the repo and create a branch: `feature/<short-desc>`
2. Follow TypeScript strict typing and existing style
3. Run tests locally and open a PR with a clear description

See `CONTRIBUTING.md` (recommended) for full guidelines.

## License & Support

This project includes a `license` file in the repository root. For commercial support, consult Syncfusion's support channels.

## SEO & Metadata

- Meta description (<=160 chars): "TypeScript quick-start: Syncfusion EJ2 PivotView demo with FieldList, GroupingBar, and CalculatedField — sample code & build scripts."
- Suggested topics: `syncfusion`, `ej2`, `typescript`, `pivot-table`, `pivotview`, `pivottable`, `quickstart`, `example`.

---

Last updated: 2026-02-02
