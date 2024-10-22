# TokopediaCase
The dataset that we used in this case contains 4 tables:
[customer_detail](https://drive.google.com/file/d/1vGkvIBs30dYItfbIplDc2eTJkLKrYaJS/view?usp=sharing)
[order_detail](https://drive.google.com/file/d/11Ekay2elqMoD6KpNxnKI9n3PJldRober/view?usp=sharing)
[payment_detail](https://drive.google.com/file/d/1Nl5qVB95tVq2qYizIFQV_nyYySw1WOWl/view?usp=sharing)
[sku_detail](https://drive.google.com/file/d/11AS-dlvpWdZBzLrw98rDFx0tk3PD1Hjf/view?usp=sharing)

In SQL, we use the dataset to:

**Analyze Transaction**
1. Identify the month with the highest transaction volume in 2021

    a. To show total transactions per month and sorted from largest to smallest transactions

         ```
          SELECT SUM(after_discount) total_transaksi,
             MONTH(order_date) month_order
          FROM order_detail
          WHERE is_valid = 1
          AND YEAR(order_date) = '2021'
          GROUP BY MONTH(order_date)
          ORDER BY SUM(after_discount) DESC`


    b. To show total transactions across all months in 2021
       
         SELECT SUM (after_discount) total_transaksi, 
              MONTH(order_date)month_order
          FROM order_detail
          WHERE is_valid = 1 
          AND YEAR (order_date) = '2021'
          GROUP BY MONTH(order_date)
          ORDER BY MONTH(order_date) ASC`

3. Identify category with highest sales in 2022

SELECT SUM(od.after_discount)nilai_transaksi, sd.category
FROM order_detail od JOIN sku_detail sd ON od.idSku = sd.idSku
WHERE od.is_valid = 1 AND order_date BETWEEN '2022-01-01' AND '2022-12-31'
GROUP BY sd.category
ORDER BY SUM(after_discount) DESC

SELECT SUM(after_discount)total_nilai_transaksi22 
FROM order_detail



