# 📊 Zomato Dataset & File Structure Overview

## 📂 Datasets Profile

### 📋 Raw Dataset Characteristics
*   **Source Format:** Uncleaned CSV metadata listing regional food marketplace transactions.
*   **Data Footprint:** Large-scale messy text dataset spanning across multiple regional file breaks.
*   **System Impact:** High storage requirements; raw columns contain text anomalies that cause data type conversion failures and heavy dashboard calculation lag.

---

## 🗺️ File Structure Data Catalog


| SI.No | Property | Description |
| :--- | :--- | :--- |
| **1** | **url** | The direct web hyperlink to the restaurant's active profile page on the Zomato platform. |
| **2** | **address** | The complete physical street address where the merchant kitchen is located. |
| **3** | **name** | The registered business name of the restaurant partner. |
| **4** | **online_order** | Categorical text flag identifying if the restaurant accepts digital delivery mobile orders (`Yes` / `No`). |
| **5** | **book_table** | Categorical text flag identifying if table booking reservations are enabled (`Yes` / `No`). |
| **6** | **rate** | Raw customer rating score out of 5, containing unparsed text anomalies like `"4.1/5"`, `"NEW"`, or `"-"`. |
| **7** | **votes** | The total cumulative integer count of customer engagement reviews and votes submitted for the venue. |
| **8** | **phone** | Registered contact mobile or landline numbers for the merchant location. |
| **9** | **location** | The specific geographic neighborhood or sub-locality inside the metropolitan market. |
| **10** | **rest_type** | The operational segment format of the merchant (e.g., Casual Dining, Quick Bites, Cafe, Delivery). |
| **11** | **dish_liked** | Unstructured text strings capturing popular food items highly reviewed by app consumers. |
| **12** | **cuisines** | Comma-separated text strings parsing the culinary profiles offered by the kitchen. |
| **13** | **approx_cost** | Float value estimating the average transaction cost/check size for two dining customers. |
| **14** | **reviews_list** | Raw text logs containing nested arrays of user feedback text strings and individual reviewer ratings. |
| **15** | **menu_item** | List arrays containing catalog items available on the restaurant's digital app menu. |
| **16** | **listed_in_type** | The macro business channel category mapping the listing (e.g., Delivery, Dine-out, Buffet, Nightlife). |
| **17** | **listed_in_city** | The primary regional administrative city cluster grouping the surrounding neighborhoods together. |

---

## 🛒 Platform Service Types (Meal Categories)
Inside the `listed_in_type` column, platform transactions are split into these specific customer channels:

*   **Delivery:** Mobile app checkout where a delivery partner transports food to a residential or corporate address.
*   **Dine-out:** Traditional walk-in restaurant visits where users consume food physically on-site.
*   **Desserts & Cafes:** Specialized snack, bakery, and beverage-focused customer checkout routines.
*   **Buffet:** High-value, fixed-price unlimited dining options.
*   **Drinks & Nightlife / Pubs and Bars:** High-margin premium entertainment segments focused on reservation-based foot traffic.

---

## ⚡ Cleaned & Optimized Datasets Profile

### 🛠️ Optimizations Applied via Power Query:
*   **Column Elimination:** Safely dropped redundant, heavy columns like `phone` and `url` to shrink file compression size.
*   **String Delimiter Splitting:** Transformed text fractions like `"4.1/5"` into pure numeric decimals to unlock the `AVERAGE()` engine.
*   **Null-Value Mapping:** Structured anomalies like `"NEW"` or `"-"` to database `null` (Blanks) so they do not introduce statistical biases into neighborhood quality scores.
*   **Data Modeling Readiness:** Appended fragmented files into a single, unified star-schema fact model with an isolated measure container table.

### 📈 Business & Analysis Benefits:
*   **Faster Processing:** Eliminates visualization memory crashes and speeds up dashboard cross-filtering.
*   **Design Cleanliness:** Erases empty white blocks inside heatmaps and matrices by cleanly handling sparse data matrices.
*   **Airtight Modeling:** Ready for advanced DAX metrics and professional, executive-level portfolio review.
