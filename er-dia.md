erDiagram

BOOK ||--o{ COPY : has
BOOK }o--o{ AUTHOR : written_by
BOOK }o--o{ GENRE : classified_as
BOOK }o--|| AGE_RATING : rated_as

COPY }o--|| LOCATION : stored_in
COPY ||--o{ LOAN : involved_in
USER ||--o{ LOAN : makes

BOOK {
    int book_id PK
    int rating_id FK
    string title
    string original_title
    int publication_year
    string publisher
    int page_count
    text description
    date created_at
}

AUTHOR {
    int author_id PK
    string last_name
    string first_name
    string middle_name
    int birth_year
    int death_year
    string country
    string special_notes
    string author_type
}

GENRE {
    int genre_id PK
    string name
    text description
}

AGE_RATING {
    int rating_id PK
    string code
    int min_age
    text description
}

COPY {
    int copy_id PK
    int book_id FK
    int location_id FK
    string inventory_number
    date acquisition_date
    numeric purchase_price
    numeric estimated_value
    string condition
    text special_notes
    boolean is_available
}

LOCATION {
    int location_id PK
    string room
    string furniture
    string shelf
    text description
}

USER {
    int user_id PK
    string last_name
    string first_name
    string middle_name
    date birth_date
    string email
    string phone
    string role
    boolean is_active
}

LOAN {
    int loan_id PK
    int copy_id FK
    int user_id FK
    date loan_date
    date due_date
    date return_date
    boolean age_check_passed
    text notes
}
