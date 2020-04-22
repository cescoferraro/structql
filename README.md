# structql

Easily generate graphl type from struct tags

	type Token struct {
		Code string `json:"code"`

		Max int `json:"max"`

		Valid bool `json:"valid"`

		Expiry time.Time `json:"expiry"`

		Data Data `json:"data"`
	}

	type Data struct {
		Name string `json:"name"`

		Trys int `json:"trys"`

		Valid bool `json:"valid"`

		Expiry time.Time `json:"expiry"`
	}

#### Defining Querys:
	"token": &graphql.Field{
		Type: structql.GenerateType(Token{}),
		Resolve: func(p graphql.ResolveParams) (interface{}, error) {
			return Token{
				Code:   "super-secret",
				Max:    2,
				Valid:  false,
				Expiry: time.Now(),
				Data: Data{
					Name:   "yay",
					Trys:   40,
					Valid:  true,
					Expiry: time.Now(),
				},
			}, nil
		},
	},


![image](https://user-images.githubusercontent.com/6259987/79978873-fe8ecc00-8476-11ea-8468-bdedeae39685.png)
