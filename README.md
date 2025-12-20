# SmartCompanion Data Format

This repository holds a specification of the data format for SmartCompanion apps. In addition examples are provided to demonstrate app features.

## Examples

 - AI-generated multilanguage tour of animal stations
 - German language audiotour through the town "Bruck an der Großglocknerstraße" © by Leon Schwaiger

## Specification

### Station

A station represents a specific point of interest within a tour or guide.

| Name | Datatype | Description | Mandatory |
|---|---|---|---|
| `id` | `string` | A unique identifier for a station, this is the same for all translations | ✅ |
| `language` | `string` | The language code of the station entry | ✅ |
| `title` | `string` | The title of the station | ✅ |
| `subtitle` | `string` | The subtitle of the station | |
| `number` | `string` | The station number, usable for identifaction of a station by humans | ✅ |
| `description` | `string` | A textual description of the station | |
| `latitude` | `number` | The latitude of the station to display on a map | |
| `longitude` | `number` | The longitude of the station to display on a map | |
| `images` | `Array<string>` | An array of asset identifiers to reference images of the station | ✅ |
| `audios` | `Array<string>` | An array of asset identifiers to reference audio files corresponding to the station | |

#### Example

```json
{
  "id": "s1",
  "language": "de",
  "number": "1",
  "title": "Bär",
  "subtitle": "",
  "audios": [
    "a1de"
  ],
  "images": [
    "i11",
    "i12"
  ]
}
```

### Asset

An asset represents a piece of media or content used within the application, such as an audio file, video, or other downloadable resource.

| Name | Datatype | Description | Mandatory |
|---|---|---|---|
| `id` | `string` | A unique identifier of an asset, this is the same for all translations | ✅ |
| `language` | `string` | The language code of the asset, if translations are available |  |
| `title` | `string` | The title of an asset, e.g. the title of an audio | |
| `duration` | `number` | The duration in seconds of an audio or video | |
| `filename` | `string` | The filename of the asset, without a path | ✅ |
| `externalUrl` | `string` | The URL of the asset file for download | ✅ |

#### Example

```json
{
  "id": "a3en",
  "filename": "a3en.mp3",
  "externalUrl": "https://smartcompanion-app.github.io/sample-data/animals/assets/a3en.mp3",
  "language": "en"
}
```

### Text

All texts in the app can be translated into any of the supported languages. Within the app’s code, only keys are used as identifiers for text snippets. These keys are replaced with the appropriate text based on the user’s selected language.

| Name | Datatype | Description | Mandatory |
|---|---|---|---|
| `language` | `string` | The language code of the translation | ✅ |
| `kev` | `string` | The key of the text, as used inside the apps | ✅ |
| `value` | `number` | The human readable text, as identified by language and key | ✅ |

#### Example

```json
{
  "language": "en",
  "key": "menu-language",
  "value": "Change language"
}
```

### Language

Specifies the languages in which the guide is available. Users can select their preferred language.

| Name | Datatype | Description | Mandatory |
|---|---|---|---|
| `title` | `string` | The title of the language, e.g., English, Deutsch, Italiano, ... | ✅ |
| `language` | `string` | The language code, e.g., `en`, `de`, `it`, ... | ✅ |

#### Example

```json
{
  "title": "English",
  "language": "en"
}
```

### Pin

A string array containing four-digit PIN codes. This provides a simple mechanism that allows the operator to require visitors to enter a PIN— for example, a PIN that is issued only upon payment of a fee.

#### Example

```json
["1234", "5577"]
```

### Tour

By including tours with designated stations in the audio guide, visitors would receive clearer guidance and enjoy a more structured, informative experience.

| Name | Datatype | Description | Mandatory |
|---|---|---|---|
| `id` | `string` | A unique identifier of the tour, this is the same for all translations | ✅ |
| `title` | `string` | The title of the tour | ✅ |
| `language` | `string` | The language code, e.g., `en`, `de`, `it`, ... | ✅ |
| `default` | `boolean` | One tour is defined as the default tour | ✅ |
| `number` | `string` | A tour could have a number as an identifier for humans | |
| `description` | `string` | A tour can have a description | |
| `stations` | `Array<string>` | An array of ordered station numbers to list all stations | ✅ |
| `images` | `Array<string>` | An array of asset identifiers to relate images to the tour | ✅ |

#### Example

```json
{
  "language": "en",
  "id": "tour1",
  "number": "1",
  "title": "Historic city walk",
  "description": "Discover the city in a scenic walk with explanations",
  "duration": "60 minutes",
  "stations": [
    "1",
    "2",
    "3",
    "4",
    "5"
  ],
  "images": [
    "image123"
  ],
  "default": true
}
```

### Server

An array of strings of IP addresses to identify servers to download data within a internal Wifi instead of the internet. This would enhance the download speed of visitors and reduce the outbound internet traffic.
