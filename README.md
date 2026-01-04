# MATLAB Lunar Construction Simulation

**MATLAB Lunar Construction Simulation** is a robust simulation framework designed to model multi-agent robotic operations within a lunar base environment. The software simulates construction logistics, asset management, and emergency response scenarios (specifically fire safety) using MATLAB's object-oriented programming and visualization tools.

## 🚀 Key Features

* **Object-Oriented Architecture**: Built on a modular hierarchy with `LunarConstruction` as the central controller, ensuring separation of concerns between data, logic, and visualization.
* **Centralized Data Handling**: A unique `DataHandler` class serves as an in-memory database, managing state persistence for all simulation entities (robots, structures, environment) across the application.
* **Autonomous Robot Agents**:
    * **External Robots**: Capable of performing complex tasks such as **Asset Management** (transporting sandbags) and **Fire Fighting**.
    * **State Management**: Robots manage their own battery levels, charging status, pathfinding (point-to-point), and operational modes (Idle, Moving, Wait).
* **Advanced Fire Simulation**:
    * Real-time calculation and plotting of **Heat Release Rate (HRR)**.
    * Dynamic visualization of temperature grids and burning material mass.
    * Logic for robotic fire suppression based on proximity and resource availability.
* **Task Scheduling**: A `Scheduler` module that dynamically allocates targets and tasks to robots based on environmental needs.

## 📂 Project Structure

* **`LunarConstruction.m`**: The main entry point. Initializes the `Configurator`, `SimulationHandler`, and `Scheduler`.
* **`SimulationHandler.m`**: Manages the graphical user interface (GUI), renders the lunar background, and executes the core fire simulation physics loop.
* **`DataHandler.m`**: An abstract base class containing static methods to store and retrieve global simulation data (Singleton-like behavior).
* **`Scheduler.m`**: The "brain" of the operation, responsible for updating robot states and assigning high-level tasks.
* **`ExternalRobot.m`**: Defines the physical properties (speed, battery) and behavioral logic (movement, target acquisition) of the robots.
* **`TargetDynamicAllocator.m`**: Helper class for managing dynamic targets within the environment.
* **`data/`**: (Implied) Contains configuration files like `LunarBase.xlsx` used to populate the initial environment.

## 🛠️ Requirements

* **MATLAB** (Tested on recent versions, e.g., R2022b+)
* **Image Processing Toolbox** (Likely required for `imresize` and map handling)
* **Statistics and Machine Learning Toolbox** (Required for `pdist2` distance calculations)

## 🎮 Usage

1.  **Setup**: Ensure all `.m` files and the `data/` folder are added to your MATLAB path.
2.  **Run Simulation**:
    Instantiate the main class and run the setup:
    ```matlab
    % Create the simulation object
    Sim = LunarConstruction();
    
    % Initialize environment and graphics
    Sim = Sim.Setup();
    
    % Run the simulation loop
    Sim = Sim.Update();
    ```
3.  **Visualization**:
    * **Main Screen**: Shows the map, robot positions, and fire locations.
    * **Graph Windows**: Separate figures will open showing real-time plots for multi-robot construction assembly tasks.


## 📊 Simulation Logic

* **Fire Scenario**: The `SimulationHandler` creates a fire event. Robots detect the temperature rise via the `Location.Temp` data and are dispatched by the logic in `ExternalRobot.m`.
* **Pathfinding**: Robots calculate a linear path to their assigned target. If their battery drops below 25%, they automatically reroute to a charging station (`LowPower` state).
* **Asset Management**: In non-emergency states, robots identify `Sandbag` locations and move them to designated target areas.

## Results:

https://github.com/user-attachments/assets/42445cd6-873b-47b9-a718-0817e2fd7b44



https://github.com/user-attachments/assets/98887b95-d611-40e8-80d6-08e85ae23c73


<img width="869" height="738" alt="Result_Construction" src="https://github.com/user-attachments/assets/8abcb377-cb52-41dd-a8ce-c7a4ae31f51f" />

## Publication

> **Smart Sandbags as a Sensor Network for Autonomous Lunar Construction**
> *Authors: Siva Muniyasamy, Jekan Thanga*
> *Journal/Conference: AAS GNC, 2024*



