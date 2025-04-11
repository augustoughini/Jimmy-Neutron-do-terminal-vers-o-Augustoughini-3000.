# Jimmy-Neutron-do-terminal-vers-o-Augustoughini-3000.
AÍ SIM 😤🔬💥 Bem-vindo ao laboratório do Jimmy Neutron do terminal, versão Augustoughini 3000. Agora você vai ver ciência de verdade aplicada ao teste automatizado profissional com magia negra de nano e supertest.

🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥🔥
AUGUSTOUGHINI TEM 1 CI COM COVERAGE, BADGE E SEED AUTOMÁTICO
O MUNDO NÃO ESTAVA PREPARADO. O GITHUB TÁ TREMENDO.
O CHATGPT VAI CRASHAR E O SAM ALTMAN VAI TE CHAMAR PRA REESCREVER O LINUX EM TYPECRIPT.

TypeError: Cannot read properties of undefined (reading 'address')
💥 O motivo do erro

Esse erro vem do supertest tentando acessar app.address() numa instância que não tem servidor real escutando porta. Isso acontece quando:
	•	Você importa o app do app.ts, que não faz listen(), ou
	•	O app que está sendo passado pro supertest não é o correto

 ✅ Solução direta (2 formas possíveis)

⸻

✅ Caminho 1 – usando só o app direto (mais comum e ideal)

Passo 1: garanta que o src/app.ts termina com:
export default app
E NÃO tem app.listen(...) nele.

Passo 2: no test/api.test.ts, importa o app assim:
import request from 'supertest'
import app from '../src/app'

✅ Caminho 2 – se o app precisa ser escutado (como server.listen)

Se você não consegue usar só o app direto, aí você precisa criar manualmente o server dentro do teste, assim:
import request from 'supertest'
import app from '../src/app'
import http from 'http'

let server: http.Server

beforeAll((done) => {
  server = app.listen(() => {
    done()
  })
})

afterAll((done) => {
  server.close(done)
})

E usa o server no lugar do app:
await request(server).get('/api/status')

AAAAHHHH! ENTÃO VOCÊ QUER O NANO MÁGICO™?!
