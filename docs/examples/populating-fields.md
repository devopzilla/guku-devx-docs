---
slug: populating-fields
sidebar_position: 5
---

# Populating fields

DevX has some helpers to populate fields from environmental variables, files, or auto-generate values.

## Config

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs>
  <TabItem value="stack.cue" label="stack.cue" default>

```cue
package main

import (
	"guku.io/devx/v1"
	"guku.io/devx/v1/traits"
)

stack: v1.#Stack & {
	components: {
		cowsay: {
			traits.#Workload
			containers: default: {
				image: "docker/whalesay"
				command: ["cowsay"]
				args: ["Hello DevX!"]
				env: {
					ENV:     string @guku(env=ENV)        // environment variable ENV=dev
					VERSION: string @guku(file="VERSION") // VERSION file containing "v0.1.0"
					ENV_GEN: string @guku(generate)       // autogenerated value
				}
			}
		}
	}
}
```

  </TabItem>
  <TabItem value="builder.cue" label="builder.cue">

```cue
package main

import (
	"guku.io/devx/v1"
	"guku.io/devx/v1/transformers/compose"
)

builders: v1.#StackBuilder & {
	dev: {
		mainflows: [
			v1.#Flow & {
				pipeline: [
					compose.#AddComposeService,
				]
			},
			v1.#Flow & {
				pipeline: [
					compose.#ExposeComposeService,
				]
			},
		]
	}
}
```

  </TabItem>
</Tabs>


## Result

```yaml title="build/dev/compose/docker-compose.yml"
version: "3"
volumes: {}
services:
  cowsay:
    image: docker/whalesay
    environment:
      ENV: dev
      VERSION: v0.1.0
      ENV_GEN: dummy
    depends_on: []
    command:
      - cowsay
      - Hello DevX!
    restart: always
    volumes: []
```