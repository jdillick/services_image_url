# Services Image Url
Drupal Services module to add image urls to services node resource.

## Problem
By default, when you create a Drupal services endpoint with a node resource, image urls are sent as the public stream wrappers. This prevents you from using this service externally to the Drupal backend.

This module adds the full publically accessible uri for the full-size image, as well as any defined image style urls, so that the image can be used with a front-end framework or third-party site.

## Example
If my endpoint is **api** and my alias to the node resource is **node**, http://localhost:8000/api/node/1 might result in json like:


```
{
    "status": "1",
    "nid": "1",
    "uuid": "3fe4906b-b853-4ab4-9a80-13343b42e429",
    "title_field": {
        "en": [
            {
                "value": "My Node",
                "format": null,
                "safe_value": "My Node"
            }
        ]
    },
    "field_image": {
        "en": [
            {
                "fid": "7433ecd1-3236-4f55-8b20-76d549e2a3b4",
                "uid": "0",
                "filename": "146426.jpg",
                "uri": "public://146426.jpg",
                "filemime": "image/jpeg",
                "filesize": "19002",
                "status": "1",
                "timestamp": "1422021634",
                "uuid": "7433ecd1-3236-4f55-8b20-76d549e2a3b4",
                "rdf_mapping": [],
                "alt": null,
                "title": null,
                "width": "250",
                "height": "250",
            }
        ]
    },
}
```

public://146426.jpg is pretty useless outside the Drupal backend. After enabling this module, your json might like like this:

```
{
    "status": "1",
    "nid": "1",
    "uuid": "3fe4906b-b853-4ab4-9a80-13343b42e429",
    "title_field": {
        "en": [
            {
                "value": "My Node",
                "format": null,
                "safe_value": "My Node"
            }
        ]
    },
    "field_image": {
        "en": [
            {
                "fid": "7433ecd1-3236-4f55-8b20-76d549e2a3b4",
                "uid": "0",
                "filename": "146426.jpg",
                "uri": "public://146426.jpg",
                "filemime": "image/jpeg",
                "filesize": "19002",
                "status": "1",
                "timestamp": "1422021634",
                "uuid": "7433ecd1-3236-4f55-8b20-76d549e2a3b4",
                "rdf_mapping": [],
                "alt": null,
                "title": null,
                "width": "250",
                "height": "250",
                "full": "http://localhost:8000/sites/default/files/146426.jpg",
                "thumbnail": "http://localhost:8000/sites/default/files/styles/thumbnail/public/146426.jpg?itok=-2rO35WV",
                "medium": "http://localhost:8000/sites/default/files/styles/medium/public/146426.jpg?itok=7dPUIBZO",
                "large": "http://localhost:8000/sites/default/files/styles/large/public/146426.jpg?itok=VU6XEymw"
            }
        ]
    },
}
```
