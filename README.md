# Hcakathon-hostel-allotment-system



To develop a hackathon hostel allotment system using SvelteKit, the architecture must focus on client-side file processing and robust allocation logic. This solution leverages the xlsx library for parsing and generating Excel files, ensuring all processing occurs within the user's browser for privacy and speed.

1. Technical Architecture


Frontend Framework: SvelteKit with TypeScript for type safety.

Styling: Tailwind CSS for a responsive, modern UI.

Spreadsheet Engine: xlsx (SheetJS) for handling .xlsx and .csv files.

State Management: Svelte stores for managing participant and hostel data during the session.

2. Core Logic Implementation

The allocation algorithm iterates through groups based on the Gender attribute and matches them to the corresponding Hostel Type.

A. Parsing Logic

The system reads the hostel sheet into an array of objects. If Capacity is absent, it defaults to a standard value (e.g., 1). Each room entry is expanded into individual available slots.

B. Allocation Algorithm

The engine filters participants and rooms by gender. It then performs a sequential mapping:

$$\text{Allotment}(P_i) = R_j \iff \text{Gender}(P_i) = \text{Type}(R_j) \land \text{Occupancy}(R_j) < \text{Capacity}(R_j)$$
where $P$ is the participant set and $R$ is the room set.

3. Implementation Code (Svelte Component)

The following snippet represents the logic within the main route +page.svelte.

4. Key Features


Dynamic Matching: The system automatically separates the participant pool by Gender and assigns them to the appropriate <keyword>Hostel Type</keyword>.

Capacity Management: The system tracks filled slots per room object to ensure no room exceeds its defined Capacity.

Waitlist Handling: If available rooms for a specific gender are exhausted, the participant is flagged as "Waitlisted."

Instant Feedback: A preview table allows organizers to verify the allotment before generating the final OpenXML file.



FeatureImplementationSTATUS
Excel UploadFileReader + xlsx.read✅
Gender-Based LogicFiltered room selection indices✅
Capacity ConstraintsReactive occupancy counter✅
Excel Exportxlsx.writeFile✅
Responsive UITailwind Flex/Grid Layouts✅
