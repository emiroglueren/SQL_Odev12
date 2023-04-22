# ODEV 12

Merhabalar,

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.


    film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
    film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
    film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
    payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.



Kolay Gelsin.

# CEVAPLAR:

## 1.Soru:

SELECT COUNT(*) FROM film
WHERE length > 
(
	SELECT AVG(length) FROM film
);

-489

## 2.Soru:

SELECT COUNT(*) FROM film
WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);

-336

## 3.Soru:

SELECT COUNT(*) FROM film
WHERE rental_rate = (SELECT MIN(rental_rate)FROM film) AND replacement_cost = (SELECT MIN(replacement_cost)FROM film);

-15

## 4.Soru:

SELECT customer.first_name, COUNT(*) as num_of_purchases FROM customer
INNER JOIN payment ON customer.customer_id = payment.customer_id
GROUP BY customer.customer_id
ORDER BY num_of_purchases DESC;
