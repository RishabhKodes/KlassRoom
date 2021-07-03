<h1><b><u>KlassRoom</b> :A companion for student life</h1></u>

<h2><b>Problem Statement:</b></h2><p>

It can be really hard to process class lectures and take notes effectively. Also, lectures listened to at home<BR>
are very difficult to pay attention to and garner information from. Finally, lectures can be disinteresting<BR>
and can often require supplemental resources.Therefore, we created KlassRoom is built to increase<BR>
the efficiency of Study.
</p>

<h2><b> Real World Problem Aimed to Solve:</h2>
<p>It can be really hard to process class lectures and take notes effectively. Also, lectures listened to at home<br>
are very difficult to pay attention to and garner information from. Finally, lectures can be disinteresting<br>
and can often require supplemental resources. Under privileged students in their house are not getting<br>
proper environment to study or focus on the lectures taught by the teachers and then high amount of data<br>
is wasted in the surfing on the internet of the topic that was taught by the teacher in the recent class which<br>
may effect the pocket oh their parents in this pandemic situation.</p>

<h2><b> Solution</h2>
<p> To make a project that transforms your online class to Google Search ,YouTube videos,<br>
and Transcript of the whole class in form of google docs so that if you don’t able to listen
to your teacher then due to voice lagging or low internet connnectivities , you can check
the transcript afterwards.
Google Search means that it’ll find some topics that may<br> be explained by the teacher and
searches on the google to save time and find relevant material.<br>
YouTube Search means that it’ll search on the youtube to find the relevant and specific
videos on the topics taught by the teacher in most recent class.</p>

## File Structure:
>  * GoogleNLPAPI.py is used to generate the keywords from the script and process <br>the speech-to-text using the audio file. <br>

> * emailAnalysis.py is used to mail the report to you email id.
<br>

> * getYoutubeVideoLinks.py generates all the YouTube video suggestions according to keywords.
<br>

> * googleDocs.py creates a Google Doc of the transcript.
<br>

> * templates/ has all the frontend code, and static/ has some frontend resources.


## <b>Steps to run and Install:
## Installation

`pip3 install pipenv`

`pip3 install google-cloud-language`

`pip3 install SpeechRecognition`

## Run Application
$ python "KlassRoom/app.py"

### Open localhost and try the app out http://127.0.0.1:5000/