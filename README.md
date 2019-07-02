Convert Minecraft Java texture packs to Minecraft Bedrock texture packs

It supports always the latest Minecraft versions, currently:

| Minecraft | Version |
|-----------|---------|
| Java      | v1.14.x |
| Bedrock   | v1.11.x |

Older versions still usable by tags later

Currently it supports block, item and entity textures

Supported input formats are zip archives or directories

Supported output formats are mcpack archives, zip archives or directories

This library is inspired by the no longer continued [PCTexture2PE](https://github.com/rodrigojxd/PCTexture2PE)

This library is written in NodeJS, with [webpack features](https://www.npmjs.com/package/webpack)

For the graphic manipulation, it uses the [jimp library](https://www.npmjs.com/package/jimp)


# Usage

Be sure you have installed [NodeJS](https://nodejs.org) (At least the LTS version)

I recommand to use [yarn package manager](https://yarnpkg.com), but of course you can also use `npm` (Should be included in NodeJS), if you want


## CLI
Clone the git repo:
```bash
git clone https://github.com/ozelot379/ConvertMinecraftJavaTextureToBedrock
```


Switch to the working dir:
```bash
cd ConvertMinecraftJavaTextureToBedrock
```


Install the dependencies

yarn:
```bash
yarn
```
npm:
```bash
npm install
```

You can now convert your texture packs like

yarn:
```bash
yarn cli -i input/java_texture_pack.zip -o output/bedrock_texture_pack.mcpack
```
npm:
```bash
npm run cli -i input/java_texture_pack.zip -o output/bedrock_texture_pack.mcpack
```

| Parameter | Description                                           |
|-----------|-------------------------------------------------------|
| -i        | Input (Required)                                      |
| -o        | Output (Required)                                     |
| -t        | Temp directory (Default is the system temp directory) |
| -l        | Verbose log                                           |


## Direct in your code
Add it as a dependency to your `package.json`

yarn:
```bash
yarn add @ozelot379/convert-minecraft-java-texture-to-bedrock
```
npm:
```bash
npm install @ozelot379/convert-minecraft-java-texture-to-bedrock
```


Import it in your code, if you use webpack
```javascript
import ConvertMinecraftJavaTextureToBedrock from "@ozelot379/convert-minecraft-java-texture-to-bedrock";
```

or require it if you use native NodeJs
```javascript
const ConvertMinecraftJavaTextureToBedrock = require("@ozelot379/convert-minecraft-java-texture-to-bedrock").default;
```


You can now convert your texture packs in an `async function`
```javascript
const outputPath = await ConvertMinecraftJavaTextureToBedrock(input, output/*, "options"*/);
```

or handle the `Promise` direct
```javascript
ConvertMinecraftJavaTextureToBedrock(input, output/*, "options"*/).then((outputPath) => {}).catch((err) => {});
```

| Parameter       | Description                                           |
|-----------------|-------------------------------------------------------|
| input           | Input (Required)                                      |
| output          | Output (Required)                                     |
| options.tmp     | Temp directory (Default is the system temp directory) |
| options.verbose | Verbose log                                           |


Example is the [CLI script](./src/cli.js)


## Know issues
- Horse textures (Seems to convert also horse from horse2)


# Extras

## UUID
You can create the `bedrock_uuid_header` and `bedrock_uuid_module` files in your input, to keep the same uuid on repeating convertations - otherwise, random uuids are genereated each time and you need to reselect the texture pack again in the game


## Custom textures
You can put custom textures in a `bedrock_textures` directory in your input

For instance for textures, that can not be converted or are not converted correctly

This files are applied additionally before output


# License
The Minecraft Java and Bedrock products are &copy; by [Mojang](https://mojang.com/)

This library for the conversation is published by the [GPL license](https://www.gnu.org/licenses/gpl-3.0.txt)
