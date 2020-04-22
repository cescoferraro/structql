# structql

Easily create graphl type from struct tags


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
