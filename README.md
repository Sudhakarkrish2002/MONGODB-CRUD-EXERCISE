# MONGODB-CRUD-EXERCISE


CREATE OPERATION:


1) test> use library                                

//use library – To switch to (or create) the database named library.


switched to db library



2) library> db.library.books              	          

//db.library.books – To check or reference the books collection inside the library database.


library.library.books



3) library> db.books.insertOne({Title:"Wings of Fire",Author:"Dr.A.P.J Abdul Kalam",Published_year:1999})          

// db.books.insertOne – To add the book "Wings of Fire" with its details into the books collection.

{
  acknowledged: true,
  insertedId: ObjectId('6884f79c5a6ef26babd412d4')
}



4) library> db.books.insertOne({Title:"The Tata Groups",Author:"Shashank Shah",Published_year:2018})        

//db.books.insertOne  – To add another book "The Tata Groups" with its details into the books collection.

{
  acknowledged: true,
  insertedId: ObjectId('6884f9f55a6ef26babd412d5')
}



5) library> db.books.find()                          

//.find() – To display all the books stored in the books collection.

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999
  },
  {
    _id: ObjectId('6884f9f55a6ef26babd412d5'),
    Title: 'The Tata Groups',
    Author: 'Shashank Shah',
    Published_year: 2018
  }
]



READ OPERATION:


1) library> db.books.find()        							

//db.books.find() - To display all the books in the books collection.

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999
  },
  {
    _id: ObjectId('6884f9f55a6ef26babd412d5'),
    Title: 'The Tata Groups',
    Author: 'Shashank Shah',
    Published_year: 2018
  }
]



2) library> db.books.find({Author:"Dr.A.P.J Abdul Kalam"}) 		

//.find({Author:"Dr.A.P.J Abdul Kalam"}) – To display only the books written by Dr.A.P.J Abdul Kalam.

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999
  }
]



3) library> db.books.find().sort({Published_year:1}).limit(1)		

//.find().sort({Published_year:1}).limit(1) – To show the oldest published book (sorted by year in ascending order and limited to one).

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999
  }
]



UPDATE OPERATION:


1) library> db.books.updateOne({Title:"The Tata Groups"},{$set:{Published_year:2025}})    

//.updateOne({Title:"The Tata Groups"},{$set:{Published_year:2025}}) – To update the Published_year of The Tata Groups book to 2025.

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}



2) library> db.books.find()															

//.find() – To verify that the year was updated in the books collection.

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999
  },
  {
    _id: ObjectId('6884f9f55a6ef26babd412d5'),
    Title: 'The Tata Groups',
    Author: 'Shashank Shah',
    Published_year: 2025
  }
]



3) library> db.books.updateMany({},{$set:{Genere:"Mystery"}})							

//.updateMany({},{$set:{Genere:"Mystery"}}) – To add/update the Genere field as Mystery for all books.

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}



4) library> db.books.find() 															

//.find() – To confirm that the Genere field was added to all books.

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999,
    Genere: 'Mystery'
  },
  {
    _id: ObjectId('6884f9f55a6ef26babd412d5'),
    Title: 'The Tata Groups',
    Author: 'Shashank Shah',
    Published_year: 2025,
    Genere: 'Mystery'
  }
]



DELETE OPERATION:


1) library> db.books.deleteOne({Published_year:2025})					

//.deleteOne({Published_year:2025}) – To delete the book published in 2025.

{ acknowledged: true, deletedCount: 1 }

library> db.books.find()

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999,
    Genere: 'Mystery'
  }
]



2) library> db.books.insertOne({Title:"The Tata Groups",Author:"Shashank Shah",Published_year:2018})		

//.insertOne({...}) – To reinsert The Tata Groups book with the year 2018.

{
  acknowledged: true,
  insertedId: ObjectId('68850d665a6ef26babd412d6')
}



3) library> db.books.find()											

//.find() – To confirm both books are now present in the collection.

[
  {
    _id: ObjectId('6884f79c5a6ef26babd412d4'),
    Title: 'Wings of Fire',
    Author: 'Dr.A.P.J Abdul Kalam',
    Published_year: 1999,
    Genere: 'Mystery'
  },
  {
    _id: ObjectId('68850d665a6ef26babd412d6'),
    Title: 'The Tata Groups',
    Author: 'Shashank Shah',
    Published_year: 2018
  }
]



4) library> db.books.deleteMany({Published_year:{$lt:2003}})			

//.deleteMany({Published_year:{$lt:2003}}) – To delete all books published before 2003

{ acknowledged: true, deletedCount: 1 }

library> db.books.find()

[
  {
    _id: ObjectId('68850d665a6ef26babd412d6'),
    Title: 'The Tata Groups',
    Author: 'Shashank Shah',
    Published_year: 2018
  }
]



ADVANCED QUERY:


1) library> db.books.find().sort({Published_year:-1}).limit(3)      

//.find().sort({Published_year:-1}).limit(3) – To display the 3 most recently published books (sorted by year in descending order).

[
  {
    _id: ObjectId('688512125a6ef26babd412d8'),
    Title: 'MongoDb',
    Author: 'Agnel john',
    Published_year: 2025
  },
  {
    _id: ObjectId('688512465a6ef26babd412d9'),
    Title: 'NOSQL',
    Author: 'Sudhakar',
    Published_year: 2022
  },
  {
    _id: ObjectId('68850d665a6ef26babd412d6'),
    Title: 'The Tata Groups',
    Author: 'Shashank Shah',
    Published_year: 2018
  }
]



2) library> db.books.find({Title:/MongoDb|NOSQL/i})                  

//.find({Title:/MongoDb|NOSQL/i}) – To display books whose titles contain MongoDb or NOSQL (case-insensitive search).

[
  {
    _id: ObjectId('688512125a6ef26babd412d8'),
    Title: 'MongoDb',
    Author: 'Agnel john',
    Published_year: 2025
  },
  {
    _id: ObjectId('688512465a6ef26babd412d9'),
    Title: 'NOSQL',
    Author: 'Sudhakar',
    Published_year: 2022
  }
]
