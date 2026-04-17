# STAR S.H.I.P. (SMS Hub for Information Processing)

The generational and socioeconomic divide in technological literacy significantly hinders the transition from paper-based records to digital infrastructure. This is especially true in underserved communities, where limited access to modern hardware, a lack of high-speed internet, and the steep learning curve of complex software leave educators reliant on fragmented data that is incompatible with modern analytical methods.

**STAR S.H.I.P.** bridges this gap by introducing an SMS-based data collection and visualization. We can empower educators to build comprehensive digital profiles through the tools they already use—ensuring a future where every teacher is just one SMS away.

---

## Technology Stack

The team has developed a functional SMS integrated with AI prototype to prove project feasibility. To optimize performance and handle token limitations, the system utilizes an **Extract, Load, Transform (ELT)** data integration architecture.

### **Backend & Infrastructure**
* **Core Framework:** Next.js
* **Database & Persistence:** Supabase (PostgreSQL)
* **SMS Integration:** HttpSMS API (Aggregator)
* **Web App Deployment:** Vercel

### **Frontend & Data Visualization**
* **Geospatial Mapping:** Leaflet.js (Heatmap)
* **Data Presentation:** HTML5, CSS, Next.js (Tabulated Data)

---

## Final Prototype App Flow

### **Phase 1: Initialization & Onboarding**
The process begins with institutional coordination. STAR staff receives official teacher IDs and phone numbers from partner organizations, issuing a unique **access code** and a designated system phone number to the educators.

### **Phase 2: Data Acquisition & Screening**
Educators converse with STAR S.H.I.P. via standard SMS, sending raw profile and professional data.
* **Ingestion:** The cellular network delivers the SMS to the **httpSMS API**, which fires a secure JSON webhook payload to the **Next.js gateway**.
* **Edge Validation:** Upon arrival, the system validates credentials (Teacher IDs) and filters invalid command formats at the edge layer to prevent backend clutter.
* *Future Roadmap:* Transitioning to Tier-1 telecommunications (Infobip) and migrating to a Python-based **FastAPI** endpoint to handle enterprise-level A2P traffic.

### **Phase 3: Data Cleaning & Normalization**
Collected data passes through a series of hardcoded input validations followed by an **AI-assisted data cleaning helper** to process conversational text before it reaches the parser.
* **Storage:** The normalized data is committed to the PostgreSQL database via Supabase.
* *Future Roadmap:* Migration to a self-hosted **vLLM (Meta Llama 3)** and **LangChain** for advanced model memory management and parsing accuracy. This planned migration to Python is essential as self-hosted AI models encounter significant latency when integrated directly with Next.js.

### **Phase 4: Real-time Analysis & Visualization**
A dedicated Next.js endpoint handles all data retrieval, ensuring the visualization layer remains decoupled from the SMS ingestion gateway.
* **Extraction:** The API executes secure queries against the PostgreSQL database, parsing records into structured JSON.
* **Visualization:** Data is served to a **Leaflet.js Map** and a tabulated information dashboard.
* **Monitoring:** The dashboard polls the REST API at 5-second intervals, providing STAR administrators with a live, real-time view of nationwide educator profiles and regional needs.

---

## Our Vision
Overall, **STAR S.H.I.P.** aims to empower and address a complex system of connections through a data-driven framework. By supporting educators from all across the nation, we are ensuring a future where digital inclusion is not limited by internet connectivity, but enabled by a single text message.
