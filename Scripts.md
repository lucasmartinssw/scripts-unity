# Scripts - Desenvolvimento de Jogos Unity

## Movimento (Horizontal e Vertical)

```csharp
transform.Translate(Input.GetAxis("Horizontal") * velocidade * Time.deltaTime, 0, 0);
transform.Translate(0, Input.GetAxis("Vertical") * velocidade * Time.deltaTime, 0);
```

## Rotacionar

```csharp
transform.Rotate(0, 0, velocidadeRotacao * Time.deltaTime);
```

## Instancionar objetos dinamicamente 

```csharp
public GameObject objeto1;
Instantiate(objeto1, transform.position, transform.rotation);
```

## Destruir outro objeto
```csharp
void OnCollisionEnter2D(Collision2D other)
{
    if (other.gameObject.CompareTag("inimigo"))
    {
        Destroy(other.gameObject);
    }
}
```