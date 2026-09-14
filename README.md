# Common — NaturaPulse Shared Module

Modul basis bersama (Swift Package) untuk aplikasi iOS **NaturaPulse**. Modul ini memuat seluruh lapisan yang dipakai lintas-fitur, sehingga tiap modul fitur cukup bergantung ke `Common`.

## Isi

- **Generic protocols** — `UseCase`, `Repository`, `RemoteSource`, `Mapper`, dan struct generic `Interactor` (Combine-based).
- **Domain** — entities (`Species`, `WeatherContext`, `Location`, dll), `AppError`, repository protocols, dan seluruh use case.
- **Data** — implementasi GBIF / Open-Meteo / Realm: DTO, data source, mapper, repository impl.
- **Core** — `APIClient` (Alamofire + Combine), `RealmProvider`.
- **DesignSystem** — Colors, Typography, Spacing, Components, Motion (shimmer/haptics).
- **Localization** — `Localizable.strings` (en/id) + helper `String.localized` (via `Bundle.module`).
- **DI** — `CommonAssembly` (Swinject).

## Products

| Product | Kegunaan |
|---|---|
| `Common` | library utama |
| `CommonTestSupport` | fake repository + `Species.stub` untuk test target |

## Kebutuhan

- iOS **26.5+**
- Swift 5 language mode
- Dependencies: Alamofire, Swinject, RealmSwift, Kingfisher (di-resolve otomatis via SPM)

## Instalasi (Swift Package Manager)

Tambahkan ke `Package.swift` Anda:

```swift
dependencies: [
    .package(url: "https://github.com/<username>/NaturaPulse-Common.git", from: "1.0.0")
],
targets: [
    .target(
        name: "YourFeature",
        dependencies: [
            .product(name: "Common", package: "NaturaPulse-Common")
        ]
    )
]
```

Atau di Xcode: **File ▸ Add Package Dependencies…** lalu masukkan URL repository ini.

## Lisensi

MIT — lihat [LICENSE](LICENSE).
