# abx-go

Android Binary XML (ABX) file parser in Go.

Reference: https://cs.android.com/android/platform/superproject/+/master:frameworks/base/core/java/com/android/internal/util/BinaryXmlPullParser.java

#### Usage

```go
package main

import (
	"os"
	"log"
	"bytes"
	"encoding/xml"

	"github.com/sagernet/abx-go"
)

func main() {
	content, err := os.ReadFile("your.xml")
	if err != nil {
		log.Fatalln(err)
	}
	reader, ok := abx.NewReader(bytes.NewReader(content))
	if !ok {
		log.Fatalln("not abx file")
	}
	decoder := xml.NewTokenDecoder(reader)
	// ...
}
```