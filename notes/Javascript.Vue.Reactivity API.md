---
id: yloqqaae81btzqdmio8fw00
title: Reactivity API
desc: ''
updated: 1698656893357
created: 1698650716284
---

# Vue - Reactivity API

## Ref

- ref can use both primitive value and objects

```javascript
<script setup>
import { ref } from 'vue'

const numberRef = ref(0);           // OK
const objectRef = ref({ count: 0 }) // OK
</script>

<template>
	{{ numberRef.value }}
</template>
```

### watch


## Reactive