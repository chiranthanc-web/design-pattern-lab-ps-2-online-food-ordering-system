# 🍽️ CraveWave — Online Food Ordering System Architecture

An end-to-end, high-performance architecture specification and interactive prototype for a modern online food ordering and delivery system, complete with native **StarUML (`.mdj`)** models and an aesthetic glassmorphism web interface.

---

## 📁 Project Structure

```text
online-food-ordering-system/
│
├── OnlineFoodOrderingSystem.mdj   # Complete StarUML Model file (Clean, colored & pre-rendered)
├── index.html                     # Aesthetic dark glassmorphism web prototype
├── build_complete_mdj.py          # Python automation script to generate/update .mdj models
└── README.md                      # Architecture documentation & design pattern breakdown
```

---

## 🎨 StarUML Design Models (`.mdj`)

The project file [`OnlineFoodOrderingSystem.mdj`](./OnlineFoodOrderingSystem.mdj) includes pre-rendered, color-coded visual diagrams configured for immediate inspection:

### 1. Domain Architecture (Class Diagram)
A simplified, orthogonal $3 \times 3$ grid with distinct functional color palettes:
* 🟦 **Customer & User Domain (`#e3f2fd`)**: `Customer` entity managing addresses, cart sessions, and reviews.
* 🟧 **Restaurant & Catalog Domain (`#fff3e0` / `#fff8e1`)**: `Restaurant` and `MenuItem` handling menus, item availability, and prep estimates.
* 🟩 **Cart & Order Domain (`#e8f5e9` / `#c8e6c9`)**: `Cart` and `Order` managing item lines, calculations, and order statuses.
* 🟪 **Payment & Telemetry Domain (`#f3e5f5` / `#ede7f6`)**: `Payment` and `DeliveryTracking` recording transaction receipts and live driver coordinates.
* 🟫 **Logistics Domain (`#e0f2f1`)**: `DeliveryAgent` tracking fleet availability and task acceptance.

### 2. System Use Cases Diagram
Clean functional columns mapping 3 primary actors to essential use cases:
* **Customer**: Browse Food, Manage Cart, One-Tap Payment, Live GPS Tracking.
* **Restaurant**: Manage Menu Catalog, Accept/Reject Incoming Orders, Update Prep Milestones.
* **Delivery Agent**: Accept Pickup Task, Stream Location Pings, Confirm Dropoff Delivery.

### 3. Order & Fulfillment Sequence Diagram
Clean message lifelines across `Customer` $\rightarrow$ `App System` $\rightarrow$ `Restaurant` $\rightarrow$ `Delivery Driver` executing checkout, kitchen ticket printing, automated dispatching, and doorstep handover.

---

## 🧠 Software Design Patterns Applied

| Pattern | Type | Real-World Application in System |
|---|---|---|
| **State Pattern** | Behavioral | Governs the strict progression of the `Order` lifecycle (`Created` $\rightarrow$ `Kitchen Preparing` $\rightarrow$ `Rider En Route` $\rightarrow$ `Delivered`). Eliminates messy `if/else` checks and prevents illegal actions (e.g., cancelling an order once food is cooking). |
| **Strategy Pattern** | Behavioral | Powers pluggable payment processors (`CardPaymentStrategy`, `ApplePayStrategy`, `UPIStrategy`, `CashOnDeliveryStrategy`) and dynamic delivery fee algorithms without modifying order logic. |
| **Observer Pattern** | Behavioral | Manages live WebSocket telemetry: when a courier streams new GPS coordinates, customer and kitchen client dashboards update in real time without polling. |
| **Facade Pattern** | Structural | Wraps stock validation, coupon discounts, payment authorization, and dispatching into an atomic one-tap checkout API. |
| **Composite Pattern** | Structural | Treats individual dishes and combo meals (e.g., *Burger + Fries + Drink*) uniformly for taxation, pricing, and allergen filtering. |

---

## 🌐 Web Prototype (`index.html`)

An interactive dark-mode glassmorphic web application demonstrating the architecture in action:

* **Dark Glassmorphic UI**: Radial gradient backdrop accents, frosted glass cards (`backdrop-filter: blur(20px)`), and typography powered by *Plus Jakarta Sans* and *Playfair Display*.
* **Live Order Telemetry Widget**: Simulates the **Observer & State Patterns** with an active pulsing beacon, live countdown timer, and an animated order progress bar (`Placed` $\rightarrow$ `Kitchen` $\rightarrow$ `En Route` $\rightarrow$ `Delivered`).
* **Slide-out Cart & Checkout Drawer**: Demonstrates the **Facade & Strategy Patterns** with real-time tax/fee calculations and interactive payment strategy toggles.
* **Live Search Filter**: Client-side instant dish search and dietary tag filtering.

---

## 🚀 Getting Started

### Opening the StarUML Project
1. Open **StarUML** on your computer.
2. Select **File → Open** and navigate to:
   ```
   online-food-ordering-system/OnlineFoodOrderingSystem.mdj
   ```
3. The **Class Diagram** will load on the main canvas.
4. To view other diagrams, open the **Model Explorer** on the right side panel and double-click:
   * `System Use Cases - Overview`
   * `Order & Delivery Sequence`

### Viewing the Web Prototype
Double-click [`index.html`](./index.html) or open it directly in any modern browser (Chrome, Edge, Firefox, Safari).

---

## 🛠️ Regenerating / Customizing Diagrams

The diagrams can be updated or regenerated programmatically using Python:

```bash
python build_complete_mdj.py
```

This updates the model elements, layout coordinates, and visual styling.

