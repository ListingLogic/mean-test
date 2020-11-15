<h1>Listing Logic Developer Test</h1>

**Install the Sample App**

- Clone this repo to your local machine<br>
CMD to the project folder<br>
docker-compose up -d<br>

- The sample app will run at localhost:3000<br>

- To view / edit running code.<br>
Open the project in your code editor<br>
The app uses a watcher. The UI will update when code is changed.<br>
TRY CHANGING THIS => modules/core/client/views/home.client.view.html<br>


- To view / edit the db.<br>
In your database editor create a connection to localhost:2717

**HINTS:**

- In the sample app Sign Up as a new user.<br>
Refresh your db editor view. Find the user in the Users Collection.<br>
Replace the existing role with 'admin'<br>
Explore all sample app features as admin<br>

**Deploy app on webhost using docker**

**Requirement**

- webhost + docker with docker filesharing enabled for the project folder<br>

**Install the App**

- copy project folder to machine<br>
cmd to project<br>
docker-compose up -d

- Your test app will run at <your host domain/ip>:3000

- If db seed is required<br>
In your database editor create a connection to <your host domain/ip>:2717<br>
Seed data using your database editor