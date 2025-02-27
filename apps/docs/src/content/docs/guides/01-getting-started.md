---
title: Getting Started
description: Getting started guide
---

## What is Astro AWS

Astro AWS is an [Astro](https://astro.build/) SSR adapter and constructs for deploying your Astro application to AWS.

> **IMPORTANT NOTE:** These packages only provide the bare minimum AWS CDK configuration to get your application running. Everything that does not need to be configured uses the default values AWS provides.

## Start your first Astro project

Create a new Astro project using the `create-astro` CLI then add the Astro AWS adapter.

### Using NPM

```sh
npm create astro@latest
npx astro add @astro-aws/adapter
```

### Using Yarn

```sh
yarn create astro@latest
yarn astro add @astro-aws/adapter
```

### Using PNPM

```sh
pnpm create astro@latest
pnpm astro add @astro-aws/adapter
```

## Build your Astro project

```sh
### Using NPM
npm run build

# Using Yarn
yarn build

# Using PNPM
pnpm run build
```

## Start your first AWS CDK project

### Create a new AWS CDK project using the CDK cli.

```sh
npm i -g aws-cdk

mkdir my-cdk-project
cd my-cdk-project

cdk init app --language typescript
```

### Add the `@astro-aws/constructs` package

```sh
# Using NPM
npm i @astro-aws/constructs

# Using Yarn
yarn add @astro-aws/constructs

# Using PNPM
pnpm i @astro-aws/constructs
```

### Modify `lib/hello-cdk-stack.ts` to contain the following

```ts
import { Stack } from "aws-cdk-lib/core"
import type { StackProps } from "aws-cdk-lib/core"
import { AstroAWS } from "@astro-aws/constructs"

export interface HelloCdkStackProps extends StackProps {}

export class HelloCdkStack extends Stack {
	public constructor(scope: Construct, id: string, props: HelloCdkStackProps) {
		super(scope, id, props)

		new AstroAWS(this, "AstroAWS", {
			websiteDir: "../my-astro-project",
		})
	}
}
```

### Deploy your cdk project

```sh
cdk deploy
```
