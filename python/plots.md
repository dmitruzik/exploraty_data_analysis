# -----------PLOTS--------------

# SALES BY PRODUCT CATEGORY
import matplotlib.pyplot as plt

prod_sales = df.groupby("product_name")[["revenue","profit","units_sold"]].sum().sort_values("revenue")

prod_sales.plot(kind="barh")
plt.title("Sales by Product Category")
plt.show()


<img width="649" height="453" alt="product_category" src="https://github.com/user-attachments/assets/87d8d95b-0091-4af5-af14-c9bcef3c957b" />


Business Conclusions — Product Categories
• Some product categories generate high revenue but lower profit — indicates cost pressure.
• High-profit categories should be prioritized in marketing campaigns.
• Low-margin high-volume products may be used as traffic drivers but need cost optimization.


# Sales by Geography

region_sales = df.groupby("region")["revenue"].sum().sort_values()

region_sales.plot(kind="barh")
plt.title("Revenue by Region")
plt.show()


<img width="594" height="453" alt="region" src="https://github.com/user-attachments/assets/1a8691aa-4c23-42a3-8871-8f4b20787d6b" />


Business Conclusions — Regions
• Revenue distribution across regions is uneven.
• Top regions should receive expanded logistics and marketing investment.
• Low-performing regions may indicate distribution or awareness issues.



# Sales By Country ( top 10)

country_sales = df.groupby("country")["revenue"].sum().nlargest(10)

country_sales.plot(kind="bar")
plt.title("Top 10 Countries by Revenue")
plt.xticks(rotation=45)
plt.show()

<img width="535" height="570" alt="salesByCountry" src="https://github.com/user-attachments/assets/8acd96cc-a7f4-4fde-bc6b-0d8ee033e3dc" />


Business Conclusions — Countries
• A small number of countries drive a large share of revenue.
• These markets are strategic and should be protected from competitor entry.
• Consider localized promotions in mid-tier countries to grow share.


# Sales channel analysis

channel = df.groupby("sales_channel")[["revenue","profit"]].sum()

channel.plot(kind="bar")
plt.title("Online vs Offline Performance")
plt.show()

<img width="534" height="487" alt="sales" src="https://github.com/user-attachments/assets/b157fd8b-7068-44b0-b0f2-f62cb85e1dec" />


Business Conclusions — Sales Channels
• One channel shows stronger profitability — likely more cost efficient.
• If online margin is higher → scale digital strategy.
• If offline revenue is higher → improve retail conversion.



# Shipping time Analysis

df["ship_days"] = (df["ship_date"] - df["order_date"]).dt.days
# by product
df.groupby("product_name")["ship_days"].mean().sort_values().plot(kind="barh")
plt.title("Avg Shipping Time by Product")
plt.show()

<img width="649" height="435" alt="shipping" src="https://github.com/user-attachments/assets/0dc57c52-d362-4c41-a6b2-82ac4aae01ed" />

Business Conclusions — Delivery Speed
• Some categories have longer fulfillment times — possible supply chain bottlenecks.
• Faster-shipping products may improve customer satisfaction and repeat purchases.



# Profit VS Shipping time

df.plot.scatter("ship_days","profit")
plt.title("Profit vs Shipping Time")
plt.show()


<img width="576" height="455" alt="profitVsShipping" src="https://github.com/user-attachments/assets/753c040c-4001-4303-8ebd-637cfa9e28c6" />


Business Conclusions — Profit vs Delivery Time
• Weak correlation suggests delivery delay does not strongly reduce profit per order.
• However, customer experience risk still exists — monitor churn separately.


# Top 5 products by revenue

top_products = (
    df.groupby("product_name")["revenue"]
      .sum()
      .nlargest(5)
      .index
)

df["month"] = df["order_date"].dt.to_period("M")


pivot_prod = df.pivot_table(
    index="month",
    columns="product_name",
    values="revenue",
    aggfunc="sum"
)

pivot_top = pivot_prod[top_products]

pivot_top.plot()
plt.title("Revenue Trend — Top 5 Product Categories")
plt.ylabel("Revenue")
plt.show()

<img width="576" height="455" alt="top5Revenue" src="https://github.com/user-attachments/assets/f9698240-fd6e-4a62-9aad-5e90216a28cc" />


Business Conclusions — Time Trends
• Revenue shows trend patterns indicating growth/decline periods.
• Peaks may correspond to promotions or seasonality.
• Planning inventory for peak months is recommended.



# Weekday Analysis
df["weekday"] = df["order_date"].dt.day_name()

# Sales by weekday
df.groupby("weekday")["revenue"].sum().plot(kind="bar")
plt.title("Revenue by Weekday")
plt.show()

<img width="547" height="521" alt="weekday1" src="https://github.com/user-attachments/assets/0508ef5a-1762-4edc-a4c9-b5717b78df25" />


# Product sysonality
top_products = (
    df.groupby("product_name")["revenue"]
      .sum()
      .nlargest(5)
      .index
)

df_top = df[df["product_name"].isin(top_products)]

pivot_week = df_top.pivot_table(
    index="weekday",
    columns="product_name",
    values="revenue",
    aggfunc="sum"
)
weekday_order = [
    "Monday","Tuesday","Wednesday",
    "Thursday","Friday","Saturday","Sunday"
]

pivot_week = pivot_week.reindex(weekday_order)
pivot_week.plot(kind="bar")
plt.title("Weekday Seasonality — Top 5 Products")
plt.xlabel("Weekday")
plt.ylabel("Revenue")
plt.xticks(rotation=45)
plt.show()

<img width="576" height="455" alt="top5Revenue" src="https://github.com/user-attachments/assets/030f3089-6ec5-4648-a5a0-7abf8a5703a9" />

<img width="554" height="508" alt="weekday2" src="https://github.com/user-attachments/assets/a5770b5f-fef1-4dc5-8b83-69b8c4a5cd2d" />

Business Conclusions — Weekly Seasonality
Revenue seasonality differs across top product categories. 
Some products peak on weekdays, suggesting business demand, while others show stronger weekend performance, indicating consumer-oriented purchasing behavior. 
This insight can guide promotion timing and inventory planning.

