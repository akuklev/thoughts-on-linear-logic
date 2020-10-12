Tentative definition of linear logic without negation
-----------------------------------------------------

Permutation:
```
 Γ, A, B, Δ ⊢ Σ       Γ ⊢ Σ, A, B, Ξ 
————————————————     ————————————————     
 Γ, B, A, Δ ⊢ Σ       Γ ⊢ Σ, B, A, Ξ

```

Basic:
```
               Γ ⊢ Σ, A   A, Δ ⊢ Ξ
————————Ax    —————————————————————Cut
 A ⊢ A             Γ, Δ ⊢ Σ, Ξ
```

Logical (Multiplicatives, i.e. internalize commas and turnstile):
```
 Γ, A, B ⊢ Σ        Γ ⊢ A, B, Σ
==============     ===============     
 Γ, A ⊗ B ⊢ Σ       Γ ⊢ A ⅋ B, Σ

 Γ, A ⊢ B, Σ         Γ ⊢ Σ, A   B, Δ ⊢ C
——————————————L⊸    ——————————————————————R⊸
 Γ ⊢ A ⊸ B, Σ         Γ, A ⊸ B, Δ ⊢ Σ, C
```

Now we have a MLL without negation and constants. Let's add interesting exponentials:

Exponentials:
```
A → B := !A ⊸ B
A ⋉ B := ?A ⅋ B
```


Tentative definition of λ⅋-calculus for that logic
--------------------------------------------------

Introduction rule for linear implication (obviously proves L⊸)
```
   Γ, x : A ⊢ e : B, Σ
——————————————————————————
 Γ ⊢ (x̅ : A; expr) : B, Σ
```

But we can also prove R⊸:
```
 Γ ⊢ Σ, a : A     Δ, x : B ⊢ c : С
————————————————————————————————————————–––—
  Γ, f : A ⊸ B, Δ ⊢ Σ, (x̅ : B; c)(f a) : C
```

Split rule for linear implication:
```
 Γ ⊢ p : A ⊸ B, u : C    Δ, x : B ⊢ e : A, Σ
——————————————————————————————————————————————————————————
 Γ, Δ ⊢ (x̅ : B <- e; u)p : C, Σ 
```
