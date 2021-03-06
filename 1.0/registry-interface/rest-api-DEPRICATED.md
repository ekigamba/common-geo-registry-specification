
# Single GeoObject
GeoObjects can be queried to & from the common geo-registry.

| path  |  Method  |  params  | description  |
|---|---|---|---|
|  /geoobject  |  GET  | Required: <ul><li>uid=string</li></ul>  |  Get a GeoObject by id.  |
|  /geoobject  |  POST  | Required: <ul><li>geoobject=object</li></ul>  |  Create a GeoObject.  |
|  /geoobject  |  PUT  | Required: <ul><li>geoObject=object</li></ul>  |  Update a GeoObject.  |

### Example
```
www.domain.com/geoobject?id=99999999
```
```
www.domain.com/geoobject?geoObject={
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [0, 0]
  },
  "properties": {
    "uid": "123",
    "code": "Valley Health",
    "type" : "HEALTHFACILITY",
    "status" : "ACTIVE",
    "featureAttributes" : [{
      "facilityType" : "CLINIC",
      "numberOfBeds" : 32
    }]
  }
}
```
```
www.domain.com/geoobject?geoObject={
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [0, 0]
  },
  "properties": {
    "uid": "123",
    "code": "Valley Health",
    "type" : "HEALTHFACILITY",
    "status" : "ACTIVE",
    "featureAttributes" : [{
      "facilityType" : "CLINIC",
      "numberOfBeds" : 32
    }]
  }
}
```

# GeoObjects By Relationship
GeoObject can be queried based on relationships to other GeoObjects.

| path  |  Method  |  params  | description  |
|---|---|---|---|
|  /childgeoobjects  |  GET  |  Required: <ul><li>parentUid=string</li> <li>childrenTypes=string[]</li> <li>recursive=boolean </li></ul>  |  Get all direct child GeoObjects of a specific GeoObject.  |
|  /parentgeoobjects  |  GET  |  Required: <ul><li>childUid=string</li> <li>parentTypes=:string[]</li> <li>recursive=:boolean </li></ul>  |  Get all direct parent GeoObjects of a specific GeoObject.  |

### Example
```
www.domain.com/childgeoobjects?parentUid=999999&childrenTypes=[type1,type2,type3]&recursive=false
```
```
www.domain.com/parentgeoobject?childUid=999999&parentTypes=[type1,type2,type3]&recursive=false
```

# GeoObject UIDs
Get list of valid UIDs for use in creating new GeoObjec The Common Geo-Registry will only accept newly created GeoObjects with a UID that was issued from the Common GeoRegistry.

| path  |  Method  |  params  | description  |
|---|---|---|---|
|  /geoobjectuids  |  GET  |  Required: <ul><li>numberOfUids=number</li> </ul>  |  Get list of valid UIDs.  |

### Example
```
www.domain.com/geoobjectuids?numberOfUids=20
```

# GeoObject Types
GeoOjectType objects that define the given list of types.

| path  |  Method  |  params  | description  |
|---|---|---|---|
|  /geoobjecttypes  |  GET  |  Required: <ul><li>types=string[]</li> </ul>  |  Get list of valid GeoObject types.  |

### Example
```
www.domain.com/geoobjecttypes?types=[type1,type2,type3]
```
