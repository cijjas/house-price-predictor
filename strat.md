

# one hot encoding

```

    # List of amenity columns to convert to binary
    amenity_columns = [
        'Cisterna', 'AccesoInternet', 'BusinessCenter', 'Gimnasio', 'Laundry',
        'Calefaccion', 'SalonDeUsosMul', 'AireAC', 'Recepcion', 'Estacionamiento',
        'Jacuzzi', 'AreaJuegosInfantiles', 'Chimenea', 'Ascensor', 'SalonFiestas',
        'Seguridad', 'Pileta', 'Cocheras', 'PistaJogging', 'EstacionamientoVisitas',
        'Lobby', 'LocalesComerciales', 'SistContraIncendios', 'AreaParrillas',
        'CanchaTennis', 'AreaCine'
    ]

    # Convert amenities to binary (0/1)
    for col in amenity_columns:
        if col in df_model.columns:
            df_model[f'{col}_binary'] = (
                (df_model[col].astype(str).str.lower().isin(['sí', 'si', 'yes', '1', '1.0'])) |
                (pd.to_numeric(df_model[col], errors='coerce') > 0)
            ).astype(int)
            df_model = df_model.drop(columns=[col])  # Remove original amenity column

```