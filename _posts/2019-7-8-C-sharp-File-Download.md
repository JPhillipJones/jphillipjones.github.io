---
layout: post
title: Downloading a File with C#
---

The below accompanies the previous example and is for downloading file with .Net C#.  The file in this case was saved as binary data in a SQL database.  Short and simple.

<h3>C#</h3>

        [HttpGet]
        [Route("DownloadFile/{Id}", Name = "DownloadFile")]
        public FileResult DownloadFile(int Id)
        {
            //Call to db to retrieve the file data record including a
            //"Binary" field that contains the bytes of the actual file
            var att = _data.RetrievFile(Id);

            return File(att.Binary, new MediaTypeHeaderValue(att.GetContentHeaderType(att.FileName)).ToString(), att.FileName);
        }
