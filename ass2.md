# Assignment2 Setup

Setting up a new web application project from scratch with a Python Flask backend and a simple HTML, CSS, and JavaScript frontend using Bootstrap involves several steps. Here’s a step-by-step guide to get you started:

### Step 1: Set Up Your Project Environment

1. **Create a Project Directory**:

   ```bash
   mkdir my_project
   cd my_project
   ```

2. **Create and Activate a Virtual Environment** (optional but recommended):

   - For macOS:
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```
   - Use Conda: https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html

3. **Install Flask**:
   ```bash
   pip install Flask
   ```

### Step 2: Set Up Flask Backend

1. **Create a Flask Application**:

   - Create a new Python file `app.py`:
   - Tutorial:
   - https://www.geeksforgeeks.org/flask-creating-first-simple-application/

     ```python
        # Importing flask module in the project is mandatory
        # An object of Flask class is our WSGI application.
        from flask import Flask

        # Flask constructor
        app = Flask(__name__, static_folder='static')

        # The route() function of the Flask class is a decorator,
        # which tells the application which URL should call
        # the associated function.
        @app.route('/')
        # ‘/’ URL is bound with hello_world() function.
        def serve_index():
            return send_from_directory(app.static_folder, 'index.html')

        # main driver function
        if __name__ == "__main__":
            app.run(host='127.0.0.1', port=8080, debug=True)
     ```

   - This code initializes a Flask app and sets up a basic route to serve an HTML page.

### Step 3: Set Up Frontend

1. **Create Your HTML Template**:

   - Create a folder structure within your project directory:
     ```bash
     mkdir static
     ```
   - In the `static` folder, create `index.html`, `script.js`, `style.css`, and folder `images`:

     ```html
     <!DOCTYPE html>
     <html>
       <head>
         <title>My Project</title>
         <meta charset="utf-8" />
         <meta name="viewport" content="width=device-width, initial-scale=1" />
         <link rel="stylesheet" href="../static/style.css" />
         <script src="../static/script.js"></script>

         <!-- Bootstrap -->
         <link
           href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
           rel="stylesheet"
         />
         <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
       </head>

       <body>
         <h1>Hello, world!</h1>
       </body>
     </html>
     ```

2. **Set Up CSS and JavaScript**:

   - Add your custom CSS and JavaScript files in file `style.css` and `script.js` separately.

3. **Set Up Bootstrap**:

   - Tutorial: https://getbootstrap.com/docs/5.3/getting-started/introduction/
   - Get started by including Bootstrap’s production-ready CSS and JavaScript via CDN without the need for any build steps. Include Bootstrap’s CSS and JS. Place the `<link>` tag in the `<head>` for our CSS, and the `<script>` tag for our JavaScript bundle. In file `index.html`:

     ```html
     <!DOCTYPE html>
     <html>
       <head>
         <title>My Project</title>
         <meta charset="utf-8" />
         <meta name="viewport" content="width=device-width, initial-scale=1" />
         <link rel="stylesheet" href="../static/style.css" />
         <script src="../static/script.js"></script>

         <!-- Bootstrap -->
         <link
           href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
           rel="stylesheet"
         />
         <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
       </head>

       <body>
         <h1>Hello, world!</h1>
       </body>
     </html>
     ```

   - Sample: https://www.w3schools.com/bootstrap5/

     ```html
     <!DOCTYPE html>
     <html>
       <head>
         <title>My Project</title>
         <meta charset="utf-8" />
         <meta name="viewport" content="width=device-width, initial-scale=1" />
         <link rel="stylesheet" href="../static/style.css" />
         <script src="../static/script.js"></script>

         <!-- Bootstrap -->
         <link
           href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
           rel="stylesheet"
         />
         <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
       </head>

       <body>
         <div class="container-fluid p-5 bg-primary text-white text-center">
           <h1>My First Bootstrap Page</h1>
           <p>Resize this responsive page to see the effect!</p>
         </div>

         <div class="container mt-5">
           <div class="row">
             <div class="col-sm-4">
               <h3>Column 1</h3>
               <p>
                 Lorem ipsum dolor sit amet, consectetur adipisicing elit...
               </p>
               <p>
                 Ut enim ad minim veniam, quis nostrud exercitation ullamco
                 laboris...
               </p>
             </div>
             <div class="col-sm-4">
               <h3>Column 2</h3>
               <p>
                 Lorem ipsum dolor sit amet, consectetur adipisicing elit...
               </p>
               <p>
                 Ut enim ad minim veniam, quis nostrud exercitation ullamco
                 laboris...
               </p>
             </div>
             <div class="col-sm-4">
               <h3>Column 3</h3>
               <p>
                 Lorem ipsum dolor sit amet, consectetur adipisicing elit...
               </p>
               <p>
                 Ut enim ad minim veniam, quis nostrud exercitation ullamco
                 laboris...
               </p>
             </div>
           </div>
         </div>
       </body>
     </html>
     ```

   - Usage Tutorial:
     - https://www.w3schools.com/bootstrap5/
     - https://getbootstrap.com/docs/5.3/customize/overview/

### Step 4: Frontend and Backend Interaction

In this step, we will establish a way for the frontend (HTML, CSS, JavaScript) to interact with the backend (Flask) through HTTP requests. We will send form data from the frontend to the backend, process it in Flask, and send a response back to the frontend.

- Frontend: We will create a simple form in the frontend and use JavaScript to send the form data to the Flask backend using the `fetch` API. In this case, we’ll use the `GET` method to send the data to the server.

  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>My Project</title>
      <meta charset="utf-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1" />
      <link rel="stylesheet" href="../static/style.css" />
      <script src="../static/script.js"></script>

      <!-- Bootstrap -->
      <link
        href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
        rel="stylesheet"
      />
      <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
    </head>

    <body>
      <div class="container mt-3">
        <h2>Stacked form</h2>
        <form>
          <div class="mb-3 mt-3">
            <label for="email">Email:</label>
            <input
              type="email"
              class="form-control"
              id="email"
              placeholder="Enter email"
              name="email"
            />
          </div>
          <div class="mb-3">
            <label for="pwd">Password:</label>
            <input
              type="password"
              class="form-control"
              id="pwd"
              placeholder="Enter password"
              name="pswd"
            />
          </div>
          <div class="form-check mb-3">
            <label class="form-check-label">
              <input
                class="form-check-input"
                type="checkbox"
                id="remember"
                name="remember"
              />
              Remember me
            </label>
          </div>
          <button type="button" id="submit" onclick="submitForm()">
            Submit
          </button>
        </form>
        <div id="responseArea"></div>
      </div>
    </body>
  </html>
  ```

  - JavaScript: Sending Data to the Flask Backend. Add the following JavaScript code in the script.js file to handle the form submission and send the data to Flask using the fetch API:

  ```javascript
  function submitForm() {
    var email = document.getElementById("email").value;
    var password = document.getElementById("pwd").value;
    var remember = document.getElementById("remember").checked;

    var url = `/submit_form?email=${encodeURIComponent(
      email
    )}&password=${encodeURIComponent(password)}&remember=${remember}`;

    fetch(url)
      .then((response) => response.json())
      .then((data) => {
        console.log("Success:", data);
        document.getElementById(
          "responseArea"
        ).innerHTML = `Status: ${data.status}, Email: ${data.email}, Remember: ${data.remember}`;
      })
      .catch((error) => {
        console.error("Error:", error);
        document.getElementById("responseArea").innerHTML =
          "Failed to retrieve data.";
      });
  }
  ```

  - Backend (Flask): Receiving and Processing Data. Now, we need to set up a Flask route that listens to the `GET` request from the frontend, processes the data, and sends a response back.

  ```python
    @app.route('/submit_form', methods=['GET'])
    def submit_form():
        # Get the query parameters from the URL
        email = request.args.get('email')
        password = request.args.get('password')
        remember = request.args.get('remember') == 'true'

        # Print "success" to the server console
        print("success")

        # Optionally print out the received data for debugging
        print(f"Received email: {email}, password: {password}, remember: {remember}")

        # Return a JSON response to the frontend
        return jsonify({"status": "success", "email": email, "remember": remember})
  ```

### Step 5: Run and Test Your Application

- Back in the terminal, make sure you are in your project directory and your virtual environment is activated, then run:
  ```bash
  python app.py
  ```
- Visit `http://127.0.0.1:8080/` in your web browser to see the application.

### Step 6: Deploy to GCP
