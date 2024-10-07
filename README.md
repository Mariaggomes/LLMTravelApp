# Agent Travel App using LLM

**LLM-MLTravelPlanner** is an intelligent travel planning application created with **Machine Learning (ML)** and **Large Language Models (LLM)**. The project uses an AI agent to generate personalized and detailed travel itineraries based on user preferences. It converts suggested destinations into an interactive map that displays the visited locations with geographical precision.

## Features

- **Personalized Itinerary Generator**: The user can request detailed travel itinerary suggestions, and the system responds with a full itinerary, including specific addresses of tourist spots.
- **Coordinate Conversion**: The generated itinerary is converted into geographic coordinates (latitude and longitude) to display the locations on the map.
- **Interactive Mapping**: Locations are marked on an interactive map using the Folium library, with automatic centralization and zoom adjustment for a clear view.
- **User-Friendly Interface**: The application uses **Streamlit** to provide a simple and direct interface where users can input their destination and view the suggested itinerary in real-time.

## Technologies Used

- **Python**: Main language of the project.
- **Streamlit**: For the interactive web interface.
- **Folium**: For visualizing maps and interactive markers.
- **OpenAI API (LLM)**: For generating detailed itineraries using advanced language models.
- **Pandas**: For data manipulation.
- **Numpy**: For mathematical calculations and array operations.
- **Langchain**: For integrating and chaining language model usage and response processing.

## Project Structure

The project is divided into two main code files: `agent.py` and `app.py`.

### `agent.py`

The `agent.py` file contains the logic of the **AI agent** responsible for generating itineraries and destination coordinates, as well as calculating the geographic center of tourist spots.

- **Classes**:
  - **ItineraryTemplate**: Defines the template for the travel agent, generating a detailed itinerary based on the user’s request.
  - **MappingTemplate**: Converts the generated itinerary into a list of coordinates (latitude and longitude) for each mentioned location.
  - **CenterMapTemplate**: Calculates the geographic center of the suggested locations and adjusts the zoom level of the interactive map.
  - **Agent**: This is the main class that uses the above templates, connecting the functionalities through a chain of models (using the **Langchain** library). It coordinates itinerary generation, coordinate conversion, and map center calculation, returning all this information to the application.

- **Main Function**:
  - **get_itinerary(request)**: Executes a model chain that generates the complete itinerary with destination suggestions, their coordinates, and the geographic center of the map.

### `app.py`

The `app.py` file contains the web application built with **Streamlit**, which offers an interactive interface for users to request travel itineraries and view the results on an interactive map.

- **Functions**:
  - **initialize_session_state()**: Initializes session state variables to maintain the map’s center, zoom level, and markers.
  - **initialize_map(center, zoom)**: Creates and initializes the map using **Folium**, based on the calculated center and zoom from the agent.
  - **reset_session_state()**: Resets session variables whenever a new itinerary request is made.
  - **Interaction Button**: The user inputs a destination into the text field, clicks a button to generate the itinerary, and the agent runs the `get_itinerary` function. The generated itinerary is displayed, and the locations are shown on a map with markers.

- **Integration with `agent.py`**:
  - The `app.py` file calls the `get_itinerary` function from `agent.py` to generate the travel itinerary and corresponding geographic data, which is then displayed in the Streamlit app.

## Docker Support

The project can also be run using **Docker**. The repository includes the necessary Docker configuration files.

### Running with Docker

1. Ensure you have **Docker** and **Docker Compose** installed on your machine.
   
2. Clone this repository:

   ```bash
   git clone https://github.com/seu-usuario/LLM-MLTravelPlanner.git
   cd LLM-MLTravelPlanner
   ```

3. Build and start the services:

   ```bash
   docker-compose up --build
   ```

4. Access the application in your browser at `http://localhost:8501`.

### Docker Configuration

- The **Dockerfile** is used to define the environment and dependencies required for the application.
- The **docker-compose.yml** file orchestrates the different services:
  - It builds the application from the Dockerfile.
  - Mounts the project directory as a volume.
  - Exposes the necessary ports, such as `8501` for Streamlit and others as needed.

### How to Run the Project

### Requirements

- Python 3.7+
- OpenAI API key
- Docker (optional)

### Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/seu-usuario/LLM-MLTravelPlanner.git
   cd LLM-MLTravelPlanner
   ```

2. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate  # Windows
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Configure the OpenAI API key:

   In the `app.py` file, insert your OpenAI API key in the appropriate place:

   ```python
   agent = Agent("YOUR_OPENAI_API_KEY")
   ```

5. Run the application:

   ```bash
   streamlit run app.py
   ```

6. Access the application in your browser at `http://localhost:8501`.

## Usage Example

1. Enter the destination in the text field, such as:

   ```text
   I would like a 3-day itinerary in Paris, visiting museums and famous tourist attractions.
   ```

2. Click the "Request itinerary suggestion" button.

3. The app will display a suggested itinerary and show an interactive map with marked points.

## Author
This project was developed by Maria Gabriela Gomes. For more information or to connect, please visit my [LinkedIn profile](https://www.linkedin.com/in/maria-gabriela-gomes-27097431b?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app).


