# smsapi-go #

[![Build Status](https://travis-ci.org/smsapi/smsapi-go.svg?branch=master)](https://travis-ci.org/smsapi/smsapi-go)
[![codecov](https://codecov.io/gh/smsapi/smsapi-go/branch/master/graph/badge.svg)](https://codecov.io/gh/smsapi/smsapi-go)

A GO client for accessing smsapi.pl / smsapi.com API.

## Usage  ##
```go
import "github.com/chmurakrajowa/smsapi-go/smsapi"
```

Create new Smsapi client for smsapi.com customers:

```go
client = smsapi.NewInternationalClient(accessToken, nil)
```

Create new Smsapi client for smsapi.pl customers:
```go
client = smsapi.NewPlClient(accessToken, nil)	
```

Send Sms
```go
result, err := client.Sms.Send(context.Background(), "+48500500500", "go", "")
```

Iterate over results
```go

pageIterator := client.Contacts.GetContactsPageIterator(ctx, nil)

for {
    page, err := pageIterator.Next()

    if err != nil {
        break
    }

    for _, c := range page.Collection {
        fmt.Println(c.PhoneNumber)
    }
}
```

## Integration Tests ##

Additional integration tests can be executed by following command:

    SMSAPI_ACCESS_TOKEN= PHONE_NUMBER= make tests-e2e

## Contributing ##

Contributions are of course always welcome.

## License

This library is distributed under the Apache 2.0 license found in the LICENSE file.
