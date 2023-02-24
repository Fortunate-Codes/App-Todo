# Development

This code appears to be a Vue.js component for a todo list application. It uses the Vue.js reactivity system with ref and computed to track state, such as whether a todo item is completed or not, and filters todo items based on their completion status.

The component also includes functions to add, remove, and clear completed todo items. It allows users to drag and drop todo items to rearrange them, and has a dark mode toggle feature.

The component uses some external images, including icons for completed and cross items, and moon and sun images for the dark mode toggle.

Overall, it appears to be a functional and well-designed component for a basic todo list application.

# Todo-App

This template should help get you started developing with Vue 3 in Vite.
## Fonts Family
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,400;0,700;1,700&display=swap');

## Content

Todo

<!-- Add dynamic number --> items left

All
Active 
Completed

Clear Completed

Drag and drop to reorder list

# Front-end Style Guide

## Layout

The designs were created to the following widths:

- Mobile: 375px
- Desktop: 1440px

## Colors

### Primary

- Bright Blue: hsl(220, 98%, 61%)
- Check Background: linear-gradient hsl(192, 100%, 67%) to hsl(280, 87%, 65%)

### Neutral

### Light Theme

--Very Light Gray: hsl(0, 0%, 98%)
--Very Light Grayish Blue: hsl(236, 33%, 92%)
--Light Grayish Blue: hsl(233, 11%, 84%)
--Dark Grayish Blue: hsl(236, 9%, 61%)
--Very Dark Grayish Blue: hsl(235, 19%, 35%)

### Dark Theme

--Very-Dark-Blue: hsl(235, 21%, 11%)
--Very-Dark-Desaturated-Blue: hsl(235, 24%, 19%)
--Light-Grayish-Blue: hsl(234, 39%, 85%)
--Light-Grayish-Blue (hover): hsl(236, 33%, 92%)
--Dark-Grayish-Blue: hsl(234, 11%, 52%)
--Very Dark-Grayish-Blue: hsl(233, 14%, 35%)
--Very Dark-Grayish-Blue: hsl(237, 14%, 26%)

## Typography

### Body Copy

- Font size: 18px

### Font

- Family: [Josefin Sans](https://fonts.google.com/specimen/Josefin+Sans)
- Weights: 400, 700

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
