## Introduction

Pharmarank est une plateforme web à destination des pharmacies permettant de mettre en oeuvre rapidemement un site pour son officine. 
Dans cette optique, Pharmarank propose une API permettant d'envoyer une liste de produits (parapharmacie et OTC) afin d'alimenter automatiquement le catalogue du site (click and collect).

## Authentification

L’authentification se fait via un token qui est passé dans le champ header “X-Auth-Token” . Ce token doit être envoyé pour toutes les requêtes.

## Lister les marques

Cette interface permet de récupérer la liste des marques.

```bash
GET /open-api/brand.list
```

```php
$client = new \GuzzleHttp\Client(['base_uri' => 'https://app.pharmarank.fr']);
$response = $client->get('/open-api/brand.list', [
   'headers' => ['X-Auth-Token' => 'my-token'],
]);
$data = json_decode($response->getBody()->getContents());
print_r($data);
```

```
[
  {
    "id": 1,
    "name": "IPRAD",
    "slug": "iprad"
  },
  ...
]
```

## Envoyer les produits

Cette interface permet d'envoyer les produits sous la forme d'un tableau JSON

```bash
GET /open-api/product.list
```

```php
$client = new \GuzzleHttp\Client(['base_uri' => 'https://app.pharmarank.fr']);
$data = [
  [
    "brand_id" => 1,
    "name" => "Doliprane 1000mg",
    "image" => "http://votredomaine.com/doliprane.jpg",
    "description" => "Ici la description",
    "cip_7" => "CIP7",
    "cip_13" => "CIP13",
    "container" => "Contenant",
    "composition" => "Composition",
    "dosage" => "",
  ],
];
```

## Lister les produits

Cette interface permet de récupérer la liste des marques.

```bash
GET /open-api/product.list
```


