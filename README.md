# Shop Helper

# VUE SETUP
$ npm install
possible feedback: "found 2 high severity vulnerabilities
run npm audit fix to fix them, or npm audit for
details"

$ npm audit fix

$npm run dev

expected feedback: "Project is running at localhost:8081 webpack output is served from /dist/ 404s will fallback to /index.html"... Go to the localhost address in your browser and you should see the project

# LOCALTUNNEL SETUP

$ npm install -g localtunnel
only run this one time to install localtunnel

$ lt --port 8082
run every time to see on phone, adjust port number according to npm run dev output
