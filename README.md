<h1 align="center">PDF Reader</h1>
<p align="center">Android support 🚀</p>

This is a fork of [rn-pdf-reader-js](https://github.com/xcarpentier/rn-pdf-reader-js) with mainly UI changes compared to the original.

# Read a PDF just with JS (no native libs needed)

## Requirements

- 👉**Install react-native-webview** on your own!
- 👉**Install expo-file-system** on your own!
- 👉**Install expo-constants** on your own!
- Use it into Expo app (from expo client, Standalone app or ExpoKit app).
- Only React-Native 0.59-0.60+ support, **Expo SDK 33-36+**

## Example

```tsx
import * as React from 'react'
import { View } from 'react-native'
import PDFReader from 'rn-pdf-reader-js'

export default class App extends React.Component {
  render() {
    return (
      <PDFReader
        source={{
          uri: 'http://gahp.net/wp-content/uploads/2017/09/sample.pdf',
        }}
      />
    )
  }
}
```

See more detailed example into `App.tsx` file.

## Props

```tsx
interface Source {
  uri?: string // can be local or served on the web (ie. start with `https://` or `file://`)
  base64?: string // should start with `data:application/pdf;base64,`. A base64 encoded pdf file tends to start with `JVBERi0xL` so your complete string should look something like this: `data:application/pdf;base64,JVBERi0xL...`
  headers?: { [key: string]: string }
}

interface Props {
  source: Source
  style?: View['props']['style'] // style props to override default container style
  webviewStyle?: WebView['props']['style'] // style props to override default WebView style
  webviewProps?: WebView['props']
  noLoader?: boolean
  useGoogleReader?: boolean // If you are not worried about confidentiality
  withScroll?: boolean // Can cause performance issue
  withPinchZoom?: boolean
  customStyle?: {
    readerContainer?: CSS.Properties
    readerContainerDocument?: CSS.Properties
    readerContainerNumbers?: CSS.Properties
    readerContainerNumbersContent?: CSS.Properties
    readerContainerZoomContainer?: CSS.Properties
    readerContainerZoomContainerButton?: CSS.Properties
    readerContainerNavigate?: CSS.Properties
    readerContainerNavigateArrow?: CSS.Properties
  }
  onLoad?(): void // callback that runs after WebView is loaded
  onLoadEnd?(): void // callback that runs after WebView is loaded
  onError?(): void // callback that runs when WebView is on error
}
```

## Possibilities

| Render type         | Platform     | Source prop   |
| ------------------- | ------------ | ------------- |
| Custom PDF reader   | Android      | uri or base64 |
| Direct from WebView | iOS          | uri or base64 |
| Google PDF Reader   | Android, iOS | uri           |

## What rn-pdf-reader-js use?

- react-pdf (pdf.js)
- WebView
- Base64

## FAQ

- [Why the component doesn't render PDF?](https://github.com/xcarpentier/rn-pdf-reader-js/issues/15#issuecomment-397306743)

