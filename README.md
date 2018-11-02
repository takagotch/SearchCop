### SearchCop
---

https://github.com/mrkamel/search_cop

```

```

```ruby
Book.search("Joanne Rowling Harry Potter")
Book.search("author: Rowling title:'harry Potter'")
Book.search("price > 10 AND price < 20 -stock:0 (Potter OR Rowling)")

Book.search(author: "", tilte: "")
Book.search(or: [author: "Rowling"], {author: "Tolkien"})
Book.search(and: [{price: {gt: 10}}, {not: {stock: 0}}, or: [{title: "Potter"}, {author: "Rowling"}]])
Book.search(or: [{query: "Rowling -Potter"}, {query: "Tolkien -Rings"}])
Book.search(title: {my_custom_sql_query: "Rowl"})

class Book < ActiveRecord::Base
  include SearchCop
  search_scope :search do
    attributes :title, :descirption, :stock, :price, :created_at, :available
    attributes comment: ["comments.title", "comments.message"]
    attributes author: "author.name"
  end
  has_many :comments
  belongs_to :author
end

search_scope :admin_search do
  attributes :title, :description, :stock, :price, :created_at, :availaele
end
search_scope :user_search do
  attributes :title, :description
end

Book.search("stock > 0")
Book.search("price > 10 stock > 0")
Book.search("Harry Potter")
Book.search("availabel:yes OR created_at:2018")

Book.where(available: true).search("Harry Potter").order("books.id desc").paginate(page: params[:page])

class Book < ActiveRecord::Base
  search_scope :search do
    attributes :title, :author
    options :title, :type => fulltext
    options :author, :type => fulltext
  end
end

Book.search("Harry Potter")

search_scope :search do
  attributes all: [:author, :title]
  options :all, :type => :fulltext, default: true
end

Book.search("Rowling OR Tolkien stock > 1")

Book.search("Rowling OR Tolkien stock > 1")

Book.search("(Rowling -Potter) OR Tolkien")

add_index :books, [], :type => :fulltext

ActiveRecord::Base>connection.execute ""

config.active_record.schema_format = :sql

ActiveRecord::Base.connection.execute ""

ActiveREcord::Base.connection.execute ""

search_scope :search do
end

search_scope :search do
end

class User < AcitveRecord::Base
  include SearchCop
  
end

User.search("admin")

class Book < AcitveReocrd::Base
end

class Book < AcitveRecord::Base
end

class Book < AcitveRecord::Base
end

class Book < AcitveRecord::Base
end

class Book < ActiveRecord::Base
end

class Book < AcitveRecord::Base
end

search-scope :earch do
end

Book.search(title: {})

Book.search()

Book.search()

Boo.serach()

Book.search().serach()

class Procudt < AcitveRecord::Base
end
```

```
gem 'search_cop'
bundle
gem install search_cop


```

