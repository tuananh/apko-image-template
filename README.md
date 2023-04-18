[![Build action](https://github.com/tuananh/apko-image-template/actions/workflows/release.yaml/badge.svg)](https://github.com/tuananh/apko-image-template/actions/workflows/release.yaml)

This is a repo template for creating new container image with [melange](https://github.com/chainguard-dev/melange) & [apko](https://github.com/chainguard-dev/apko).

It comes with a [dummy melange package](hello.melange.yaml) and a default [apko image config](latest.apko.yaml). You will need to edit those files accordingly to get started.

## Usage

```bash
$ docker run --rm -it ghcr.io/tuananh/apko-image-template
```

## Signing

This image is signed with [cosign](https://github.com/sigstore/cosign). To verify, download `cosign` and run

```sh
cosign verify ghcr.io/tuananh/apko-image-template:latest \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity https://github.com/tuananh/apko-image-template/.github/workflows/release.yaml@refs/heads/main | jq
```

Expected output

<details>

```
Verification for ghcr.io/tuananh/apko-image-template:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - The code-signing certificate was verified using trusted certificate authority certificates
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/tuananh/apko-image-template"
      },
      "image": {
        "docker-manifest-digest": "sha256:4e68130405fb4d912edf7980deb1bda938f10a707c5d6df2f1ed47cb9c684900"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "458d670d1715c793a31a8e244fd040afb08145a8",
      "1.3.6.1.4.1.57264.1.4": "Build action",
      "1.3.6.1.4.1.57264.1.5": "tuananh/apko-image-template",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQChkog4XGTsg5Vp6MYWGFBp+MxjENu/gHd7DRwhTNo8bAIgV0jGGKcYEh+cxgBCC9WB1tTjsGh4yJbeqxIZcRQVQp0=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJiMTQ5NTVhZmVlYjE0ZTAyNjcyMjRmZmQyY2E2MTlmODI0NTA1MTBlMjI4NzViYjJkZmU3MDJjYzVhNDczMzVjIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUUR1NG5kWTc3Ulgvam5UbnZsUGYxNjhRd1dWaGUrUlJpaFdWaHFBNEh1elNRSWhBTk5FaWNPTGV2OU9vaUlMV0FKMTUwQ3drMW0vTkVOOEVxN21YYlBBY3ZDcCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVY3hWRU5EUW14MVowRjNTVUpCWjBsVlJtUjJZVmR0YVdnMWJ6ZEtRM2xOZVZwUWVtOXZVbmMyYlVKRmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcE5kMDVFUlRSTlJFMTVUV3BKTWxkb1kwNU5hazEzVGtSRk5FMUVUWHBOYWtreVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZUZWtOak9VUlFVbXBFZUdOU1JWSlZiWE5OTW1sTk5ITlhTemMwYWtOalZFcE9helVLYW01b1ZESkxlV2gyUTJKRlNGSkJkamd2UkZGdE9GTkJVRFpwYjBJNVZIWjFZMUJtU1RKeWVUUTRkRXd5VlhkV0wwdFBRMEpZYjNkbloxWXlUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZXVEM5bUNsQnljVzkxZDBsV2VESk5TaTlPYlVoRFMxVnZkVFZCZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGM1dVUldVakJTUVZGSUwwSkhSWGRZTkZwa1lVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVEROU01WbFhOV2hpYldkMldWaENjZ3BpZVRGd1lsZEdibHBUTVRCYVZ6RjNZa2RHTUZwVE9IVmFNbXd3WVVoV2FVd3paSFpqYlhSdFlrYzVNMk41T1hsYVYzaHNXVmhPYkV4dWJHaGlWM2hCQ21OdFZtMWplVGx2V2xkR2EyTjVPWFJaVjJ4MVRVUnJSME5wYzBkQlVWRkNaemM0ZDBGUlJVVkxNbWd3WkVoQ2VrOXBPSFprUnpseVdsYzBkVmxYVGpBS1lWYzVkV041Tlc1aFdGSnZaRmRLTVdNeVZubFpNamwxWkVkV2RXUkROV3BpTWpCM1JtZFpTMHQzV1VKQ1FVZEVkbnBCUWtGblVVbGpNazV2V2xkU01RcGlSMVYzVG1kWlMwdDNXVUpDUVVkRWRucEJRa0YzVVc5T1JGVTBXa1JaTTAxSFVYaE9la1V4V1hwak5VMHlSWHBOVjBVMFdsUkpNRTVIV210TlJGRjNDbGxYV21sTlJHZDRUa1JXYUU5RVFXRkNaMjl5UW1kRlJVRlpUeTlOUVVWRlFrRjRRMlJYYkhOYVEwSm9XVE5TY0dJeU5IZExVVmxMUzNkWlFrSkJSMFFLZG5wQlFrSlJVV0prU0Zab1ltMUdkV0ZET1doalIzUjJURmRzZEZsWFpHeE1XRkpzWWxoQ2MxbFlVbXhOUWpCSFEybHpSMEZSVVVKbk56aDNRVkZaUlFwRU0wcHNXbTVOZG1GSFZtaGFTRTEyWWxkR2NHSnFRVGRDWjI5eVFtZEZSVUZaVHk5TlFVVkpRa013VFVzeWFEQmtTRUo2VDJrNGRtUkhPWEphVnpSMUNsbFhUakJoVnpsMVkzazFibUZZVW05a1Ywb3hZekpXZVZreU9YVmtSMVoxWkVNMWFtSXlNSGRpVVZsTFMzZFpRa0pCUjBSMmVrRkNRMUZTWmtSR01XOEtaRWhTZDJONmIzWk1NbVJ3WkVkb01WbHBOV3BpTWpCMlpFaFdhR0p0Um5WaFF6bG9ZMGQwZGt4WGJIUlpWMlJzVEZoU2JHSllRbk5aV0ZKc1RIazFiZ3BoV0ZKdlpGZEpkbVF5T1hsaE1scHpZak5rZWt3elNteGlSMVpvWXpKVmRXVlhSblJpUlVKNVdsZGFla3d5YUd4WlYxSjZUREl4YUdGWE5IZFBRVmxMQ2t0M1dVSkNRVWRFZG5wQlFrTm5VWEZFUTJjd1RsUm9hMDVxWTNkYVJFVXpUVlJXYWs1NmEzcFpWRTE0V1ZSb2JFMXFVVEJhYlZGM1RrUkNhRnB0U1hjS1QwUkZNRTVYUlRSTlFqQkhRMmx6UjBGUlVVSm5OemgzUVZGelJVUjNkMDVhTW13d1lVaFdhVXhYYUhaak0xSnNXa1JCSzBKbmIzSkNaMFZGUVZsUEx3cE5RVVZOUWtSQlRVeHRhREJrU0VKNlQyazRkbG95YkRCaFNGWnBURzFPZG1KVE9UQmtWMFoxV1ZjMWIwd3lSbmRoTWpoMFlWY3hhRm95VlhSa1IxWjBDbU5IZUdoa1IxVjNUMEZaUzB0M1dVSkNRVWRFZG5wQlFrUlJVWEZFUTJjd1RsUm9hMDVxWTNkYVJFVXpUVlJXYWs1NmEzcFpWRTE0V1ZSb2JFMXFVVEFLV20xUmQwNUVRbWhhYlVsM1QwUkZNRTVYUlRSTlFqaEhRMmx6UjBGUlVVSm5OemgzUVZFMFJVVlJkMUJqYlZadFkzazViMXBYUm10amVUbDBXVmRzZFFwTlFtdEhRMmx6UjBGUlVVSm5OemgzUVZFNFJVTjNkMHBPYWtFelRtcHJNMDlFWnpCTlEyOUhRMmx6UjBGUlVVSm5OemgzUVZKQlJVaEJkMkZoU0ZJd0NtTklUVFpNZVRsdVlWaFNiMlJYU1hWWk1qbDBURE5TTVZsWE5XaGliV2QzUm1kWlMwdDNXVUpDUVVkRWRucEJRa1ZSVVVsRVFWa3lUV3BqZVU1NlozY0tZbEZaUzB0M1dVSkNRVWRFZG5wQlFrVm5VbVpFUmpGdlpFaFNkMk42YjNaTU1tUndaRWRvTVZscE5XcGlNakIyWkVoV2FHSnRSblZoUXpsb1kwZDBkZ3BNVjJ4MFdWZGtiRXhZVW14aVdFSnpXVmhTYkV4NU5XNWhXRkp2WkZkSmRtUXlPWGxoTWxwellqTmtla3d6U214aVIxWm9ZekpWZFdWWFJuUmlSVUo1Q2xwWFducE1NbWhzV1ZkU2Vrd3lNV2hoVnpSM1QwRlpTMHQzV1VKQ1FVZEVkbnBCUWtWM1VYRkVRMmN3VGxSb2EwNXFZM2RhUkVVelRWUldhazU2YTNvS1dWUk5lRmxVYUd4TmFsRXdXbTFSZDA1RVFtaGFiVWwzVDBSRk1FNVhSVFJOUW1kSFEybHpSMEZSVVVKbk56aDNRVkpSUlVObmQwbGpNazV2V2xkU01RcGlSMVYzV1ZGWlMwdDNXVUpDUVVkRWRucEJRa1pSVWxSRVJrWnZaRWhTZDJONmIzWk1NbVJ3WkVkb01WbHBOV3BpTWpCMlpFaFdhR0p0Um5WaFF6bG9DbU5IZEhaTVYyeDBXVmRrYkV4WVVteGlXRUp6V1ZoU2JFd3lSbXBrUjJ4MlltNU5kbU51Vm5WamVUZ3dUbnBKTkUxcVNYZE9WRTE0VERKR01HUkhWblFLWTBoU2VreDZSWGRuV1hOSFEybHpSMEZSVVVJeGJtdERRa0ZKUldaUlVqZEJTR3RCWkhkRVpGQlVRbkY0YzJOU1RXMU5Xa2hvZVZwYWVtTkRiMnR3WlFwMVRqUTRjbVlyU0dsdVMwRk1lVzUxYW1kQlFVRlpaVk5aY0V4SVFVRkJSVUYzUWtsTlJWbERTVkZEUmtwRmNITkpjbGxFY0hKRVdEQXpPV2d4VDBoTUNqYzBXRkpyYkhCcVNFNVpiekZaWkhKNE5FUnpURkZKYUVGTVRtZDRaSEp3V0dVNWQweG5iU3RyTkRCNldrOUlkMncyV0V0MWRqaDNSbE5FV1ZNMVUwOEtVbk5RUTAxQmIwZERRM0ZIVTAwME9VSkJUVVJCTW1kQlRVZFZRMDFSUXpsWWJtOWpNRUpLTldkNlEzZENUVGhZVjNOV1ZUVkRlR3RrV2xSWGFqTlVVd28xUzBKcVoyTlhRMHh5VjNCdlNWbHNPVTVZVVhFd2NpOVhkR1pZZFZGdlEwMUVPRGx1ZVhOaVRsSk9NRVUzTjJvM09XbzFOVXBpV1Raa2FtZ3lUSFptQ210R2QyUnZOMU4wV1VwUlNrVlBkWFEzVUZwbloxTlpRa0o1YlM5cFZYTkhaa0U5UFFvdExTMHRMVVZPUkNCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2c9PSJ9fX19",
          "integratedTime": 1681788147,
          "logIndex": 18244011,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/tuananh/apko-image-template/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Build action",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "tuananh/apko-image-template",
      "githubWorkflowSha": "458d670d1715c793a31a8e244fd040afb08145a8",
      "githubWorkflowTrigger": "schedule"
    }
  }
]  
```
</details>

## License

[MIT License](LICENSE)