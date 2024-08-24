# Real-Time Kafka Data Stream Visualization

## Project Overview

This project demonstrates a real-time system performance monitoring solution using Apache Kafka and Python. By capturing and streaming live CPU usage data from a local machine to a Kafka topic, the system enables real-time visualization and analysis using Matplotlib within a Jupyter Notebook environment. This project serves as a practical example for understanding real-time data streaming, visualization, and system performance monitoring techniques.

## Files in the Project

### 1. **Producer.py**

**Function:** 

This script actively monitors the system's CPU usage and publishes this data in real-time to a Kafka topic named 'test-topic'. The CPU usage percentage is encoded as a byte-encoded integer before being sent. Data generation and transmission occur at a frequency of 0.5 seconds (twice per second).

**Key Features:**

 * Real-time CPU Monitoring: The script continuously tracks the CPU usage of the system, providing up-to-date information.
 * Kafka Integration: It utilizes Apache Kafka to publish the CPU usage data, enabling real-time streaming and consumption by other applications.
 * Data Encoding: The CPU usage percentage is efficiently encoded as a byte-encoded integer before transmission, optimizing data size.
 * High-Frequency Updates: The script generates and sends data every 0.5 seconds, ensuring a near-continuous stream of CPU usage information.

- **Usage:**
    - To run this script, simply execute it using Python:
    
    ```bash
    python Producer.py
    ```

    - Ensure Kafka is running and the topic `'test-topic'` is created.

### 2. **Kafka_RealTime_Plot.ipynb**

**Function:** 

This Jupyter Notebook acts as a real-time data consumer and visualizer. It subscribes to the Kafka topic 'test-topic' to receive incoming CPU usage data. The received data is processed and added to a list for plotting. Matplotlib is utilized to create a dynamic line chart that updates every second, displaying the most recent 200 data points. This provides a live visualization of the system's CPU usage trends.

**Key Features:**

* Real-time data consumption from Kafka
* Data processing and storage for plotting
* Dynamic Matplotlib chart with continuous updates
  
- **Usage:**
    - Open the notebook in Jupyter and execute the cells sequentially.
    - Ensure Kafka is running and data is being produced to the `'test-topic'` topic.

### 3. **Project.ipynb**

**Function:** 

This Jupyter Notebook provides an alternative real-time visualization of CPU usage data streamed from Kafka. Like 'Kafka_RealTime_Plot.ipynb', it consumes data from the 'test-topic' and displays it in a continuously updating graph.  However, it may employ different visualization techniques or configurations (e.g., different chart types, data aggregation, or display settings) to offer a unique perspective on the system's CPU performance.

**Possible Distinctions (compared to Kafka_RealTime_Plot.ipynb):**

* May use a different chart type (e.g., bar chart, area chart)
* May aggregate data over time intervals for a smoother visualization
* May offer customizable display settings (e.g., color schemes, axis labels)
* May include additional features or analysis beyond basic plotting
  
- **Usage:**
    - Open the notebook in Jupyter and execute the cells sequentially.
    - Ensure Kafka is running and data is being produced to the `'test-topic'` topic.

## Installation Instructions

1. **Install Kafka:**

    - Download and install Apache Kafka from [Kafka's official site](https://kafka.apache.org/).
    - Start the Kafka server on your local machine:

    ```bash
    bin/zookeeper-server-start.sh config/zookeeper.properties
    bin/kafka-server-start.sh config/server.properties
    ```

2. **Create a Kafka Topic:**

    - Create the topic `'test-topic'`:

    ```bash
    bin/kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092
    ```

3. **Install Required Python Packages:**

    - Use `pip` to install the required Python packages:

    ```bash
    pip install kafka-python psutil matplotlib
    ```

## Usage Instructions

1. **Run the Producer:**

    - Start the `Producer.py` script to begin sending CPU usage data to Kafka:

    ```bash
    python Producer.py
    ```

2. **Run the Consumer and Visualization:**

    - Open either `Kafka_RealTime_Plot.ipynb` or `Project.ipynb` in Jupyter Notebook.
    - Run the cells to start consuming and visualizing the data in real-time.

## Example Output

![CPU Usage Plot](https://github.com/NikkaLuna/Real_Time_Kafka_Data_Stream_Visualization/blob/main/CPU_Usage_Plot.png)


The above image shows a sample real-time CPU usage plot generated by this project. The graph updates every second, showing the latest 200 data points.
