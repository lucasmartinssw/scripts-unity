# Scripts - Desenvolvimento de Jogos Unity

## Movimento (Horizontal e Vertical)

```csharp
transform.Translate(Input.GetAxis("Horizontal") * velocidade * Time.deltaTime, 0, 0);
transform.Translate(0, Input.GetAxis("Vertical") * velocidade * Time.deltaTime, 0);
