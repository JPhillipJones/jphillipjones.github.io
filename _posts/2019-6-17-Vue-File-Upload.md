---
layout: post
title: Uploading a File with Vue.js and C#
---

The below is a short example of a file upload in a Vue.js/.Net C# app.  The file or files get attached to the "files" portion 
of the form colection.  

<h3>HTML</h3>

        <div class="upload-btn-wrapper">
            <button class="btn">Upload a file</button>
            <input type="file" name="uploadDoc" id="uploadDoc" v-on:change="attachFile" />
            {{ attachementFileName }}
        </div>

<h3>CSS</h3>

      .upload-btn-wrapper input[type=file] {
          font-size: 100px;
          position: absolute;
          left: 0;
          top: 0;
          opacity: 0;
      }

<h3>Vue Method</h3>

      attachFile(e) {
            var v = this;
            v.attachement = e.target.files[0];
            v.attachementFileName = e.target.files[0].name;
            alert(e.target.files[0].name + " uploaded successfully");
        }
        
<h3>C#</h3>

       [HttpPost]
        [Route("UploadFile", Name = "UploadFile")]
        public async void UploadFile(IFormCollection Upload)
        {
            if (Upload.Files.Count > 0)
            {
                //If we have at least one file in the IFormCollection, then perform whatever storage actions
            }
        }
