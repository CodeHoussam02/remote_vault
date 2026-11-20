```javascript
// Prisma schema

model albums {
  AlbumId  Int      @id
  ArtistId artists  @relation("albums_ArtistId_artists")
  Title    String
  tracks tracks[] @relation("albums_tracks_AlbumId", references: [AlbumId])
}

model genres {
  GenreId  Int      @id
  Name     String?
  tracks tracks[] @relation("genres_tracks_GenreId", references: [GenreId])
}

model artists {
  ArtistId Int      @id
  Name     String?
  albumses albums[] @relation("albums_ArtistId_artists")
}

model playlists {
  Name            String?
  PlaylistId      Int              @id
  playlist_tracks playlist_track[] @relation("playlist_track_PlaylistId_playlists")
}

model playlist_track {
  PlaylistId playlists @id(strategy: NONE) @relation("playlist_track_PlaylistId_playlists")
  TrackId    tracks    @id(strategy: NONE) @relation("playlist_track_TrackId_tracks")

  @@unique([PlaylistId, TrackId], name: "sqlite_autoindex_playlist_track_1")
}

model tracks {
  AlbumId         albums?          @relation("albums_tracks_AlbumId")
  Bytes           Int?
  Composer        String?
  GenreId         genres?          @relation("genres_tracks_GenreId")
  MediaTypeId     media_types      @relation("media_types_tracks_MediaTypeId")
  Milliseconds    Int
  Name            String
  TrackId         Int              @id
  UnitPrice       Float
  invoice_itemses invoice_items[]  @relation("invoice_items_TrackId_tracks")
  playlist_tracks playlist_track[] @relation("playlist_track_TrackId_tracks")
}

model invoices {
  BillingAddress    String?
  BillingCity       String?
  BillingCountry    String?
  BillingPostalCode String?
  BillingState      String?
  CustomerId        customers
  InvoiceDate       DateTime
  InvoiceId         Int             @id
  Total             Float
  invoice_itemses   invoice_items[] @relation("invoice_items_InvoiceId_invoices")
}

model invoice_items {
  InvoiceId     invoices @relation("invoice_items_InvoiceId_invoices")
  InvoiceLineId Int      @id
  Quantity      Int
  TrackId       tracks   @relation("invoice_items_TrackId_tracks")
  UnitPrice     Float
}

model media_types {
  MediaTypeId Int      @id
  Name        String?
  tracks    tracks[] @relation("media_types_tracks_MediaTypeId", references: [MediaTypeId])
}
```