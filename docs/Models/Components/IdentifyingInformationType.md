# IdentifyingInformationType

The `type` provided determines whether you are submitting a tax identification number or some form of government-issued ID.

Reference these lists for tax identification numbers by country: [Individuals](https://apidocs.bridge.xyz/docs/individual-tax-identification-numbers-by-country), [Businesses](https://apidocs.bridge.xyz/docs/business-tax-identification-numbers-by-country)

Here is the list of acceptable government issued id documents: `drivers_license`, `matriculate_id`, `military_id`, `permanent_residency_id`, `state_or_provincial_id`, `visa`, `national_id`, `passport`

All customers must provide at least one Tax Identification Number for their issuing country. If a country cannot be found, please select `other` and ensure the `description` field is provided.

Non-U.S. `individual` customers and associated persons must include a combination of at least one Tax Identification Number and at least one photo id document such as a `passport` (with `image_front`) or a government-issued `drivers_license`. If the photo id document used is also a valid tax identification number (like a national id), it can be submitted as a single object in the `identifying_information` array; otherwise, a valid tax identification number must also be submitted as a separate object in the `identifying_information` array.



## Values

| Name                   | Value                  |
| ---------------------- | ---------------------- |
| `DriversLicense`       | drivers_license        |
| `MatriculateId`        | matriculate_id         |
| `MilitaryId`           | military_id            |
| `NationalId`           | national_id            |
| `Passport`             | passport               |
| `PermanentResidencyId` | permanent_residency_id |
| `StateOrProvincialId`  | state_or_provincial_id |
| `Visa`                 | visa                   |
| `Abn`                  | abn                    |
| `Acn`                  | acn                    |
| `Ahv`                  | ahv                    |
| `Ak`                   | ak                     |
| `Aom`                  | aom                    |
| `Arbn`                 | arbn                   |
| `Avs`                  | avs                    |
| `Bc`                   | bc                     |
| `Bce`                  | bce                    |
| `Bin`                  | bin                    |
| `Bir`                  | bir                    |
| `Bp`                   | bp                     |
| `Brn`                  | brn                    |
| `Bsn`                  | bsn                    |
| `Bvn`                  | bvn                    |
| `Cc`                   | cc                     |
| `Cdi`                  | cdi                    |
| `CedulaJuridica`       | cedula_juridica        |
| `Cf`                   | cf                     |
| `Cif`                  | cif                    |
| `Cin`                  | cin                    |
| `Cipc`                 | cipc                   |
| `Cn`                   | cn                     |
| `Cnp`                  | cnp                    |
| `Cnpj`                 | cnpj                   |
| `Cpf`                  | cpf                    |
| `Cpr`                  | cpr                    |
| `Crc`                  | crc                    |
| `Crib`                 | crib                   |
| `Crn`                  | crn                    |
| `Cro`                  | cro                    |
| `Cui`                  | cui                    |
| `Cuil`                 | cuil                   |
| `Curp`                 | curp                   |
| `Cuit`                 | cuit                   |
| `Cvr`                  | cvr                    |
| `Edrpou`               | edrpou                 |
| `Ein`                  | ein                    |
| `Embg`                 | embg                   |
| `EmiratesId`           | emirates_id            |
| `En`                   | en                     |
| `Fin`                  | fin                    |
| `Fn`                   | fn                     |
| `Gstin`                | gstin                  |
| `Gui`                  | gui                    |
| `Hetu`                 | hetu                   |
| `Hkid`                 | hkid                   |
| `Hn`                   | hn                     |
| `Ic`                   | ic                     |
| `Ico`                  | ico                    |
| `Id`                   | id                     |
| `IdBroj`               | id_broj                |
| `Idno`                 | idno                   |
| `Idnp`                 | idnp                   |
| `Idnr`                 | idnr                   |
| `If`                   | if                     |
| `Iin`                  | iin                    |
| `Ik`                   | ik                     |
| `Inn`                  | inn                    |
| `Ird`                  | ird                    |
| `Itin`                 | itin                   |
| `Itr`                  | itr                    |
| `Iva`                  | iva                    |
| `Jmbg`                 | jmbg                   |
| `Kbo`                  | kbo                    |
| `Kvk`                  | kvk                    |
| `Matricule`            | matricule              |
| `Mf`                   | mf                     |
| `Mn`                   | mn                     |
| `Ms`                   | ms                     |
| `Mst`                  | mst                    |
| `Nic`                  | nic                    |
| `Nicn`                 | nicn                   |
| `Nie`                  | nie                    |
| `Nif`                  | nif                    |
| `Nin`                  | nin                    |
| `Nino`                 | nino                   |
| `Nip`                  | nip                    |
| `Nipc`                 | nipc                   |
| `Nipt`                 | nipt                   |
| `Nit`                  | nit                    |
| `Npwp`                 | npwp                   |
| `Nric`                 | nric                   |
| `Nrn`                  | nrn                    |
| `Nrt`                  | nrt                    |
| `Ntn`                  | ntn                    |
| `Nuit`                 | nuit                   |
| `Nzbn`                 | nzbn                   |
| `Oib`                  | oib                    |
| `Orgnr`                | orgnr                  |
| `Other`                | other                  |
| `Pan`                  | pan                    |
| `PartitaIva`           | partita_iva            |
| `Pesel`                | pesel                  |
| `Pib`                  | pib                    |
| `Pin`                  | pin                    |
| `Pk`                   | pk                     |
| `Ppsn`                 | ppsn                   |
| `Qid`                  | qid                    |
| `Rc`                   | rc                     |
| `Regon`                | regon                  |
| `Rfc`                  | rfc                    |
| `Ricn`                 | ricn                   |
| `Rif`                  | rif                    |
| `Rn`                   | rn                     |
| `Rnc`                  | rnc                    |
| `Rnokpp`               | rnokpp                 |
| `Rp`                   | rp                     |
| `Rrn`                  | rrn                    |
| `Rtn`                  | rtn                    |
| `Ruc`                  | ruc                    |
| `Rut`                  | rut                    |
| `Si`                   | si                     |
| `Sin`                  | sin                    |
| `Siren`                | siren                  |
| `Siret`                | siret                  |
| `Spi`                  | spi                    |
| `Ssm`                  | ssm                    |
| `Ssn`                  | ssn                    |
| `SteuerId`             | steuer_id              |
| `Strn`                 | strn                   |
| `Tckn`                 | tckn                   |
| `Tfn`                  | tfn                    |
| `Tin`                  | tin                    |
| `Tpin`                 | tpin                   |
| `Trn`                  | trn                    |
| `Ucn`                  | ucn                    |
| `Uen`                  | uen                    |
| `Uic`                  | uic                    |
| `Uid`                  | uid                    |
| `Usc`                  | usc                    |
| `UstIdnr`              | ust_idnr               |
| `Utr`                  | utr                    |
| `Vat`                  | vat                    |
| `Vkn`                  | vkn                    |
| `Voen`                 | voen                   |
| `YTunnus`              | y_tunnus               |