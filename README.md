# go-playstore-scraper
> it provides an api to retrieve the info of any particular app.

### installing
> go get "github.com/asmsh/go-playstore-scraper"

### notes
still in beta.  
see issues for not supported app fields.

### examples

you can get the app by just specifying its app id (package name),
and it will get the app info in the default language and locale (with respect to play store).
```go
package main

import (
	"fmt"
	"github.com/asmsh/go-playstore-scraper/api/apps"
)

func main() {
	app, e := apps.GetAppByID("com.example.app")
	if e != nil {
		fmt.Println(e.Error())
	} else {
		fmt.Printf("app screenshots urls: %q\n", app.ScreenShotsUrls)
	}
}
```

or you can specify in which language and locale you want the info
```go
package main

import (
	"fmt"
	"github.com/asmsh/go-playstore-scraper/api/apps"
	"github.com/asmsh/go-playstore-scraper/engine/urls/locales"
)

func main() {
	app, e := apps.GetAppByIDAdv("com.example.app", locales.CountryUS, locales.LanguageEnglish_US)
	if e != nil {
		fmt.Println(e.Error())
	} else {
		fmt.Printf("app description: %s\n", app.Description)
	}
}
```

you can choose to retrieve only specific fields of the app info
```go
package main

import (
	"fmt"
	"github.com/asmsh/go-playstore-scraper/api/apps"
	"github.com/asmsh/go-playstore-scraper/engine/types/appField"
	"github.com/asmsh/go-playstore-scraper/engine/urls/locales"
)

func main() {
	app, e := apps.GetAppByIDAdv("com.example.app", locales.CountryUS, locales.LanguageArabic, appField.Rating)
	if e != nil {
		fmt.Println(e.Error())
	} else {
		fmt.Printf("app rating: %s\n", app.Rating)
	}
}
``` 

you can also get the info of an app using its url directly
```go
package main

import (
	"fmt"
	"github.com/asmsh/go-playstore-scraper/api/apps"
)

func main() {
	app, e := apps.GetAppByUrl("https://play.google.com/store/apps/details?id=com.example.app")
	if e != nil {
		fmt.Println(e.Error())
	} else {
		fmt.Printf("app rating histogram: %q\n", app.RatingHistogram)
	}
}
``` 

##### there are more features yet to come..