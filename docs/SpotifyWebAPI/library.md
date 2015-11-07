##SaveTracks
<span class="label label-warning">AUTH REQUIRED</span>
> Save one or more tracks to the current user’s “Your Music” library.

**Paramters**  

|Name|Description|Example|
|--------------|-------------------------|-------------------------|
|ids| A list of the Spotify IDs | `new List<String> { "3Hvu1pq89D4R0lyPBoujSv" }`

Returns a **ErrorResponse** which just contains a possible error. (`response.HasError()` and `response.Error`)

**Usage**  
```cs
ErrorResponse response = _spotify.SaveTracks(new List<string> { "3Hvu1pq89D4R0lyPBoujSv" });
if(!response.HasError())
    Console.WriteLine("success");
```

---
##SaveTrack
<span class="label label-warning">AUTH REQUIRED</span>
> Save one track to the current user’s “Your Music” library.

**Paramters**  

|Name|Description|Example|
|--------------|-------------------------|-------------------------|
|id| A Spotify ID | `"3Hvu1pq89D4R0lyPBoujSv"`

Returns a **ErrorResponse** which just contains a possible error. (`response.HasError()` and `response.Error`)

**Usage**  
```cs
ErrorResponse response = _spotify.SaveTrack("3Hvu1pq89D4R0lyPBoujSv");
if(!response.HasError())
    Console.WriteLine("success");
```

---
##GetSavedTracks
<span class="label label-warning">AUTH REQUIRED</span>
> Get a list of the songs saved in the current Spotify user’s “Your Music” library.

**Paramters**  

|Name|Description|Example|
|--------------|-------------------------|-------------------------|
|[limit]| The maximum number of objects to return. Default: 20. Minimum: 1. Maximum: 50. | `20`
|[offset]| The index of the first object to return. Default: 0 (i.e., the first object) | `0`
|[market]| An ISO 3166-1 alpha-2 country code. Provide this parameter if you want to apply Track Relinking. | `DE`

Returns a **Paging<SavedTrack>**, **SavedTrack** contains 2 properties, `DateTime AddedAt` and `FullTrack Track`

**Usage**  
```cs
Paging<SavedTrack> savedTracks = _spotify.GetSavedTracks();
savedTracks.Items.ForEach(track => Console.WriteLine(track.Track.Name));
```

---
##RemoveSavedTracks
<span class="label label-warning">AUTH REQUIRED</span>
> Remove one or more tracks from the current user’s “Your Music” library.

**Paramters**  

|Name|Description|Example|
|--------------|-------------------------|-------------------------|
|ids| A list of the Spotify IDs. | `new List<String> { "3Hvu1pq89D4R0lyPBoujSv" }`

Returns a **ErrorResponse** which just contains a possible error. (`response.HasError()` and `response.Error`)

**Usage**  
```cs
ErrorResponse response = _spotify.RemoveSavedTracks(new List<string> { "3Hvu1pq89D4R0lyPBoujSv" });
if(!response.HasError())
    Console.WriteLine("success");
```

---
##CheckSavedTracks
<span class="label label-warning">AUTH REQUIRED</span>
> Check if one or more tracks is already saved in the current Spotify user’s “Your Music” library.

**Paramters**  

|Name|Description|Example|
|--------------|-------------------------|-------------------------|
|ids| A list of the Spotify IDs. | `new List<String> { "3Hvu1pq89D4R0lyPBoujSv" }`

Returns a **ListResponse<bool>** which contains a property, `List<bool> List`

**Usage**  
```cs
ListResponse<bool> tracksSaved = _spotify.CheckSavedTracks(new List<String> { "3Hvu1pq89D4R0lyPBoujSv" });
if(tracksSaved.List[0])
    Console.WriteLine("The track is in your library!");
```

---