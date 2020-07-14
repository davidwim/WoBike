# Beam
[Beam](https://www.ridebeam.com/) is a E-Scooter sharing service that operates in the Asia-Pacific Region.

**Base URL** `https://gateway.ridebeam.com/api`

## Login

+ Request verification code
+ Use the verification code to authenticate

#### Request SMS Verification Code

The account doesn't already need to exist

**Method**: `POST`

**Path**: `/auth/phoneverification`

**Parameters**:

| Headers       | Value                                 | Mandatory |
| ------------- | ------------------------------------- | :-------: |
| Content-Type  | application/json                      | X         |
| User-Agent    | escooterapp/<latest-app-version>; ios | X         |

**The Body**:

`{"phoneNumber":"<phone-number>","countryCode":"+<country-code>"}`

As a result, you should end up with info about your Phone Number and the OTP code.

### Send back OTP code

**Method**: `POST`

**Path**: `/auth/verifycodeAndCreateUser`

**Headers**:

| Headers       | Value                                 | Mandatory |
| ------------- | ------------------------------------- | :-------: |
| Content-Type  | application/json                      | X         |
| User-Agent    | escooterapp/<latest-app-version>; ios | X         |

**The Body**:

`{"phoneNumber":"<phone-number>","countryCode":"+<country-code>","code":"<verifiaction-code>","deviceName":"iPhone8,1(iPhone 6S)"}`

As a result, you should end up with something like this:

```
     "jwtAccessToken": "JWT <long-string>",
     "refreshToken": "<long-string>",
```

## Get Scooter Locations

**Base URL** `https://gateway.ridebeam.com/api/vehicles/scooter/latlong`

**Method**: `GET`

#### Send back OTP code

**Method**: `POST`

**Path**: `/v1/login`

**Headers**:

| Headers       | Value                                 | Mandatory |
| ------------  | ------------------------------------- | :-------: |
| Content-Type  | application/json                      | X         |
| User-Agent    | escooterapp/<latest-app-version>; ios | X         |
| Authorization | JWT long-string                       | X         |
| Latitude      | latitude                              | X         |
| Longitude     | longitude                             | X         |

**Parameters**:

| Parameters | Descriptions             | Mandatory |
| ---------- | ------------------------ | :-------: |
| Latitude   | latitude                 | X         |
| Longitude  | longitude                | X         |

The output should come out something like this:

```{
                "id": 5019,
                "status": 0,
                "lastReportedBattery": 60,
                "code": "67329",
                "lastOysterHeartbeatReportTime": null,
                "lastPhoneLocationTime": "2020-07-14T03:41:52.773Z",
                "lastReportedTimeTrackerMotion": null,
                "lastOysterAfterMotionSingleReportTime": null,
                "lastPhoneLocationBLERSSI": -100,
                "bestLocation": {
                    "type": "Point",
                    "coordinates": [
                        172.56853366666667,
                        -43.54138616666667
                    ]
                },
                "serialNumber": "N4ZMA2002C0854",
                "vehicleType": 1,
                "bleMacAddress": "ce:c4:6b:35:45:4d",
                "omniIotImei": "868020030569379",
                "Tasks": [],
                "formFactor": "escooter"
            },
```
