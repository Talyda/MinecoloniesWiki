# MineColonies Wiki

A wiki for the Minecraft mod [MineColonies](https://github.com/ldtteam/minecolonies). Read it [here](https://wiki.minecolonies.ldtteam.com/)!

## Guidelines to pages

### Worker/building names
We want to avoid having to change a bazillion occurences all over the wiki in case we ever need to rename a worker or a building, for that reason there are 2 tags (`{% building /%}` and `{% worker /%}`) which you can use to write the name of the building/worker directly based on the name defined in the data files.

You can use these by doing `{% building /%}` (only directly in the building source page) OR `{% building name="<key>" %}` (when referring to a building outside of the building page itself). This setup is identical for the worker (by using `{% worker name="<key>" /%}`).

### Links
We have a lot of links in the website referring to other documentation pages, a lot of them are still configured with a manually written name + path, for example: `[Apiary](/wiki/buildings/apiary)`.

Going forwards we are using link templates, these are created using Markdoc tags.

#### Buildings
In order to write a building link you have to write: `{% building name="<key>" /%}` where the key of the building can be found in the `src/content/buildings`.

These link templates will automatically generate the path to the building aswell as use the proper name defined the in `src/content/buildings`.

#### Workers
In order to write a worker link you have to write: `{% worker name="<key>" /%}` where the key of the worker can be found in the `src/content/workers`.

These link templates will automatically generate the path to the worker aswell as use the proper name defined the in `src/content/workers`.

#### Versioned content
In order to write something that only applies to given Minecraft versions, you may use version blocks to state certain content is only visible on selected Minecraft versions.

The way you write version blocks is like this:
```
{% version range="<range>" %}
Content
{% /version %}
```

The range determines what Minecraft versions are selected and can be written in several ways:
- `1.21` - A direct Minecraft version number
- `1.21--` - Any version above or equal to 1.21
- `--1.21` - Any version below or equal to 1.21
- `1.20--1.21` - Any version between 1.20 and 1.21 (including 1.20 and 1.21 itself)

> Note: Every version number must match the `id` of any version defined in `versions.yaml`.

## Testing locally
The project can be ran locally to test if your changes work as expected. You need the following installed to be able to run it.

- Nodejs (https://nodejs.org/en/download) 23 or above
- Pnpm (https://pnpm.io/installation)

### Preparing the project
After cloning the project and having all the required tools installed you need to run:

- pnpm install

This will install all of the project dependencies defined in the `package.json`.

### Running the project
The project is served using the Astro CLI, this will start up a development server where you can test your changes.

In order to serve the project locally you have to run:

- pnpm start