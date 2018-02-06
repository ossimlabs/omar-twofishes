# OMAR Twofishes

## Usage

### Example
HTTP Request:
```
<server_protocol://<server_name/<context_path>?autocomplete=true&autocompleteBias=BALANCED&maxInterpretations=1&responseIncludes=WKT_GEOMETRY_SIMPLIFIED&query=Paris
```
HTTP Response:
```
{
    "interpretations":[
        {
            "what":"",
            "where":"paris",
            "feature":{
                "cc":"FR",
                "geometry":{
                    "center":{
                        "lat":48.85341,"lng":2.3488
                    },
                    "bounds":{
                        "ne":{
                            "lat":48.90164950000002,
                            "lng":2.416341999999929
                        },
                        "sw":{
                            "lat":48.815856999999994,
                            "lng":2.2237277313554387
                        }
                    },
                    "wktGeometrySimplified":"POLYGON ((2.410663999999997 48.878479000000084, 2.4132470000000126 48.87311550000004, 2.415399999999977 48.855270500000074, 2.416341999999929 48.84923950000007, 2.415863999999999 48.84663400000011, 2.412428000000091 48.834240000000136, 2.409102999999959 48.83430100000004, 2.400539000000151 48.83122599999996, 2.4072170000000597 48.82670950000016, 2.4003670000001307 48.82895650000012, 2.39054700000014 48.82612250000011, 2.3907491978728217 48.82599136934584, 2.3888469999999984 48.82544350000006, 2.3644140000000675 48.816078000000005, 2.355566999999894 48.815856999999994, 2.351417000000083 48.817245499999956, 2.344058000000132 48.815956500000084, 2.3320139999999583 48.81694050000016, 2.3282645000000457 48.81905000000006, 2.3137705000000324 48.82210250000003, 2.30103100000008 48.82506550000005, 2.279577999999958 48.83083349999998, 2.2695000000001073 48.82870500000007, 2.2676940000000627 48.83335100000011, 2.264225000000124 48.834106500000075, 2.26409607182444 48.83389851366775, 2.2616174197802934 48.83416647605088, 2.261453000000074 48.83402250000006, 2.254463999999814 48.83585750000003, 2.2507280000001515 48.845390500000065, 2.24064199999998 48.84886550000016, 2.238958000000082 48.84995650000002, 2.238030999999978 48.85015500000014, 2.2267080000001442 48.84875100000011, 2.2266680318156205 48.84862097506209, 2.2237277313554387 48.84862097506209, 2.224242000000004 48.85938250000015, 2.228841999999929 48.867771000000005, 2.2355310000000372 48.873382500000105, 2.2408893806174888 48.877436155980945, 2.2497669999998493 48.87546550000002, 2.253650500000049 48.874924000000135, 2.2554529999999318 48.8758165000001, 2.258868999999777 48.88055050000008, 2.2773220000000265 48.87832650000013, 2.279981500000133 48.87852850000013, 2.284281000000078 48.88576900000004, 2.319861000000003 48.90074550000003, 2.329958500000089 48.901161000000116, 2.37026400000002 48.90164950000002, 2.389417000000094 48.90118800000005, 2.3953315000000543 48.89775100000003, 2.401006000000052 48.883262500000114, 2.410663999999997 48.878479000000084))",
                    "source":"qs"
                },
                "name":"Paris",
                "displayName":"Paris, France",
                "woeType":7,
                "ids":[
                    {
                        "source":"geonameid",
                        "id":"2988507"
                    },
                    {
                        "source":"woeid",
                        "id":"615702"
                    }
                ],
                "names":[
                    {
                        "name":"Paris",
                        "lang":"en",
                        "flags":[1]
                    }
                ],
                "highlightedName":"<b>Paris</b>, France",
                "matchedName":"Paris, France",
                "id":"geonameid:2988507",
                "attributes":{
                    "population":2138551,
                    "urls":[
                        "http://uk.wikipedia.org/wiki/%D0%9F%D0%B0%D1%80%D0%B8%D0%B6",
                        "http://www.paris.fr",
                        "http://en.wikipedia.org/wiki/Paris"
                    ]
                },
                "longId":"72057594040916443",
                "parentIds":[
                    "72057594040945318",
                    "72057594040940810",
                    "72057594040896751",
                    "72057594040916442",
                    "72057594044383195"
                ]
            }
        }
    ]
}
```

### Input Params
| | | |
| - | - | - |
| URL Param | Type | Description |
| `autocomplete` | boolean | Defaults to false, whether or not to return partial- matches as if powering an autocompleter. |
| `autocompleteBias` | integer or string | i.e. `autocompleteBias=BALANCED` - influences how locally (relative to `ll` hint, if specified) and globally relevant results are mixed in autocomplete geocoding mode. Defaults to `BALANCED`. <br /> `BALANCED` - mix locally and globally relevant results (DEFAULT) <br /> `GLOBAL` - prefer globally relevant results <br /> `LOCAL` - prefer locally relevant results <br /> `NONE` - no bias
| `cc` | string | Country code which biases geocoding similar to `ll` (prefer matches in this country). Also influences name formatting -- a feature in this country will not include the country name in the displayName. |
| `debug` | integer | Specify the amount of debugging in the server response. 1 is a lot of debug info, 4 is a tremendous amount of debug info. Slows down the server a lot. |
| `lang` | string | i.e. es, en or zh. Influences what languages are used in constructing the `displayName` in the response. Defaults to en. geocoding "nyc" in with `lang=es` will suggest "Nueva York" as the best name. Additionally, the server will return all alternate names in english + this language. |
| `ll` | double,double | A comma separated double ie, 40.74,-74.0. If `query` is specified, this will be a hint to bias returned results. If `query` is not specified, it will reverse geocode this latlng. |
| `maxInterpretations` | integer | Specify the number of different interpretations of the query (or reverse geocode) that you want. Larger value means slower & bigger response. In reverse geocode mode, 0 or unset means 'unlimited' in autocomplete mode, 0 or unset means 3 in geocode mode, 0 or unset means 1. |
| `responseIncludes` | string,string,... | i.e. `responseIncludes=PARENTS,ALL_NAMES` - influences what is contained within the returned interpretations. Most of these make the response slightly slower. <br /> `ALL_NAMES` - include all names, not just in english + lang <br /> `DISPLAY_NAME` - controls if we should fetch parents to construct a string like "New York, New York, US" for legacy reasons, this is automatically turned on for geocode queries for now. It's mainly here because reverse geocode clients often don't need it <br /> `EVERYTHING` - includes everything listed below <br /> `PARENTS` - include the parent features of a venue (ie NY state, US inside the interpretation for 'new york city') <br />  `PARENT_ALL_NAMES` - same, but for parents <br /> `REVGEO_COVERAGE` - for ll+radius revgeo queries, turns on computing the percentage overlap between the circle query and the feature polygon. slow-ish <br /> `S2_COVERING` - include S2 covering of polygon boundary as a list of S2 cell ids if available <br /> `S2_INTERIOR` - include S2 interior covering of polygon boundary as a list of S2 cell ids if available <br /> `WKB_GEOMETRY` - include polygon boundary geometry in WKB format if available <br /> `WKB_GEOMETRY_SIMPLIFIED` - include simplified polygon boundary geometry in WKB format if available <br /> `WKT_GEOMETRY` - include polygon boundary geometry in WKT format if available <br /> `WKT_GEOMETRY_SIMPLIFIED` - include simplified polygon boundary geometry in WKT format if available |
| `query` | string | For geocoding. The server will attempt to geocode as much of the string (from left to right) as possible. |
| `radius` | integer | Defaults to 0 (point reverse geocode). If specified along with ll, will return all polygons touched by the circle defined by ll+radius. In strict geocoding mode, used for determining containment. |
| `strict` | boolean | Defaults to false. if true, only returns results within the `cc`, bounds and `ll`+`radius` specified. |
| `woeHint` | integer,integer,... | i.e. `woeHint=7,10` or `woeHint=TOWN,ADMIN3` - look at the YahooWoeType enum for total range of values. Biases the geocoder to prefer features of these types. |
| `woeRestrict` | comma separated list of YahooWoeType integers or enum names | Same arguments as `woeHint`. Geocoder will only return features of these types. |
