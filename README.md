Backend Test - Park a bike in Paris
---

## How we review

**We value quality over feature-completeness**. It is fine to leave things aside provided you call them out in your project's README. The goal of this code sample is to help us identify what you consider production-ready code. You should consider this code ready for final review with your colleague, i.e. this would be the last step before deploying to production.

The aspects of your code we will assess include:

* **Architecture**: how clean is the separation between responsibilities
* **Clarity**: does the README clearly and concisely explains the problem and solution? Are technical tradeoffs explained?
* **Correctness**: does the application do what was asked? If there is anything missing, does the README explain why it is missing?
* **Code quality**: is the code simple, easy to understand, and maintainable?  Are there any code smells or other red flags? Does object-oriented code follows principles such as the single responsibility principle? Is the coding style consistent with the language's guidelines? Is it consistent throughout the codebase?
* **Security**: are there any obvious vulnerability?
* **Testing**: how thorough are the automated tests? Will they be difficult to change if the requirements of the application were to change? Are there some unit and some integration tests?
	* We're not looking for full coverage (given time constraint) but just trying to get a feel for your testing skills.
* **Technical choices**: do choices of libraries, databases, architecture etc. seem appropriate for the chosen application?

## Project

Let's say you're creating an app giving you the nearest place where you can park your bike in Paris.
It supports regular bike parkings, but also Velib stations in case you are riding a Velib.

For the following request:

```txt
POST /nearest-parkings/bike
{
    lat: 40.30011,
    lng: -1.39440
}
```

we expect a response like
```txt
{
    parkings: [
        { kind: "VELIB", lat: 40.130, lng: -1.49599 },
        { kind: "PUBLIC", lat: 40.6544, lng: -1.59699 },
        { kind: "PUBLIC", lat: 40.599, lng: -1.56999 }
    ]
}
```

Kind can be VELIB or PUBLIC depending on the data source

Under the hood, the data should be managed by two microservices:
- **Velib service**: for Velib Stations data
- **Parkings service**: for public parking spaces

A gateway will perform the request and aggregate the responses in the final form.

## Requirements

For this project, we'd like you to use:
- NodeJS
- Typescript
- Any NoSQL database

Apart from that list, you may use any tool you consider useful.

It is not required to use infrastructure tools like Docker.


## Data

The Velib stations file can be found here:
https://opendata.paris.fr/explore/dataset/velib-emplacement-des-stations/information/

The public parking spaces file can be found here:
https://opendata.paris.fr/explore/dataset/stationnement-voie-publique-emplacements/table/?disjunctive.regpri&disjunctive.regpar&disjunctive.typsta&disjunctive.arrond&disjunctive.zoneres&disjunctive.tar&disjunctive.locsta&disjunctive.parite&disjunctive.signhor&disjunctive.signvert&disjunctive.confsign&disjunctive.typemob&disjunctive.zoneasp&disjunctive.stv&disjunctive.prefet&refine.regpri=2+ROUES&refine.regpar=V%C3%A9los&refine.regpar=Mixte


## Sending the project

When you're done, you can push your code in a private repository on Github and invite @maximelebastard as a contributor
