# Offline_Chatbot_via_SMS
This project is an **AI-powered chatbot prototype** that works completely **offline via SMS**. The chatbot receives user queries through a GSM modem, processes the queries using **GPT-4o from AIxplain**, and sends responses back via SMS. It is designed to support areas where no Internet connection is required , leveraging local language support, and internet access is limited.
## 📌 Key Features
- **Offline AI Chatbot:** Works without internet using GSM.
- **SMS Support:** Handles queries and sends responses over SMS.
- **Queue-Based Processing:** Uses message queues to handle multiple queries efficiently.
- **AI-Powered Responses:** Integrates with AIxplain's **GPT-4o** for generating answers.
- **Automatic Acknowledgments:** Sends instant acknowledgment upon receiving a query.
- **Message Chunking:** Splits long responses into 160-character chunks to comply with SMS limits.
## 🏗️ Architecture

1. **User Interaction:** User sends a question via SMS.
2. **Message Queue:** Incoming messages are added to a queue.
3. **AI Processing:** AIxplain's GPT-4o processes the query and automatically generates a response.
4. **Response Handling:** The response is split into chunks and sent back to the user via SMS.


## 📦 Requirements

- **Python Version:** Python 3.11.3 (IDLE platform).
- **GSM Modem:** With an active SIM card (preferably Airtel)
- **AIxplain API Key:** To access GPT-4o
- **Dependencies:**
  - `pyserial` — Communication with the GSM modem
  - `logging` — Event tracking and error handling
  - `aixplain` — Integration with AIxplain for AI model access
  - `queue` — Queue management for incoming messages
  - `threading` — Handling simultaneous tasks like message listening and processing
  - `re` — Regex for splitting messages into SMS-friendly chunks
  - `subprocess` — Executing external commands, if required
  - `time` — Managing delays and timing operations
  - `os` — (Optional) Environment handling

## ⚙️ Setup Instructions

1. **Get the Components:**
   - Buy all the necessary components: GSM modem, active SIM card (preferably Airtel),USB to SERIAL adapter, and a computer with Python installed.

2. **Set Up the GSM Modem:**
   - Insert the SIM card into the GSM modem.
   - Check if the modem is working:
     - Call the SIM card number. If it rings or a green light blinks every three seconds, the modem is ready.

3. **Check the COM Port:**
   - Open "Device Manager" on your computer and check the "Ports (COM & LPT)" section.
   - Note the COM port number (e.g., COM2 or COM4) and update it in the code where the serial port is initialized:
     ```python
     ser = serial.Serial('COM2', 9600, timeout=5)
     ```

4. **Verify GSM Connection:**
   - Use a tool like PuTTY to send the `AT` command.
   - If the modem replies with `OK`, the GSM connection is set up correctly.

5. **Install Python and Dependencies:**
   - Install Python 3.11.3.
   - Install required Python libraries using:
     ```bash
     pip install pyserial logging aixplain
     ```

6. **Configure AIxplain:**
   - Get your API key and model ID from the AIxplain platform.
   - Update the `api_key` and `model_id` variables in the code to ensure the chatbot connects to GPT-4o:
     ```python
     api_key = "YOUR_API_KEY"
     model_id = "YOUR_MODEL_ID"
     ```

7. **Run the Chatbot:**
   - Open a terminal, navigate to the project folder, and run:
     ```bash
     python chatbot.py
     ```
   - The chatbot will start listening for incoming messages.

8. **Test the Chatbot:**
   - From any mobile phone (Android or button phone), send an SMS to the GSM modem’s SIM card number with a query.
   - The chatbot should reply with the processed answer.

## 🛠️ Troubleshooting

- **GSM Modem Not Detected:** Check the serial port (COM2/COM4) and update it in the code.
- **No Response from AI:** Verify the AIxplain API key and ensure the model ID is correct.
- **SMS Not Sending:** Ensure the GSM modem has proper signal and the SIM card is active.

## 📬 Acknowledgments

- AIxplain for providing AI models.
