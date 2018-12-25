# go-playstore-scraper
> it provides an api to retrieve the info of any particular app.

### examples

you can get the app by just specifying its app id, 
and it will get the app info in the default language and local
```go
app, e := api.GetAppByID("com.example.app")
	if e != nil {
		fmt.Println(e.Error())
	} else {
		fmt.Printf("app screenshots urls: %q\n", app.ScreenShotsUrls)
	}
```

or you can specify in which language and local you want the info
```go
app, e := api.GetAppByIDAdv("com.example.app", locales.CountryUS, locales.LanguageEnglish_US)
	if e != nil {
		fmt.Println(e.Error())
	} else {
		fmt.Printf("app description: %s\n", app.Description)
	}
```

you can also get the info of an app using its url directly
```go
app, e := api.GetAppByUrl("https://play.google.com/store/apps/details?id=com.example.app")
	if e != nil {
		fmt.Println(e.Error())
	} else {
		fmt.Printf("app rating histogram: %q\n", app.RatingHistogram)
	}
```

##### there are more features yet to come..