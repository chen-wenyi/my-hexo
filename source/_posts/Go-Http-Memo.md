---
title: Go Http Memo
date: 2019-09-12 14:40:06
categories:
- Go
tags:
- Http
---

# start a tcp server on port 8080
```
http.ListenAndServe(":8080", nil) // addr, handler
```

# router and handler
```
http.HandleFunc("/file/upload", handler.UploadHandler)
```

# http redirect
```
http.Redirect(w, r, "/file/upload/suc", http.StatusFound)
```

# Get querystring from url
```
func GetFileMetaHandler(w http.ResponseWriter, r *http.Request) {
	r.ParseForm()
  filehash := r.Form["filehash"][0] // would be a list from queryString filehash = [...]

  // Get the first one
  // filehash := r.Form.Get("filehash")
  ...
}
```

# Header Set for file download
```
w.Header().Set("Content-Disposition", "attachment;filename=\""+fileMeta.FileName+"\"")

```

