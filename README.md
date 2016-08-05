# Youtube MP3 server

A simple flask server that returns the direct link of audio given the youtube video.
It also provides the feature to search youtube and return search results in a RESTful manner.

Serves as the backend for [music genie](https://github.com/bxute/musicgenie).

[![Launch on OpenShift](http://launch-shifter.rhcloud.com/button.svg)](https://openshift.redhat.com/app/console/application_type/custom?cartridges%5B%5D=python-2.7&initial_git_url=https%3A%2F%2Fgithub.com%2Faviaryan%2Fyoutube%2Dmp3%2Dserver.git&name=youtube%2Dmp3%2Dserver)

## Running

```
pip install -r requirements.txt
python app.py
```

----

## API

#### Get audio url from video

Send a GET request to `/g/<video_id>` where `video_id` is youtube video id. (Example `/g/8oGZTbeEhv4`)

A successful response is of the following format.

```js
{
  "status": 0,
  "url": "https://some.com/long/url"
}
```

The error response follows the same format but sets `status` to non-zero value.


#### Get youtube search results

Send a GET request to `/search` with query param `q=<search term>`. (Example `/search?q=Back%20In%20Time`)

Response is of the following format.

```js
[
  {
    "id": "zaSZE194D4I",
    "length": "3:33",
    "thumb": "http://img.youtube.com/vi/zaSZE194D4I/0.jpg",
    "time": "3 years ago",
    "title": "Pitbull - Back in Time",
    "uploader": "PitbullVEVO",
    "views": "20,328,744"
  },
]
```