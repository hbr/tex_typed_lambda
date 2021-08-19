********************************************************************************
Strong Normalization
********************************************************************************


From the quasinormalization theorem we get the following result:
    All valid types T can be reduced to one of

    - a syntactical kind ::

        all (x₀:A₀) (x₁:A₁) ... : s

    - a syntactical type ::

        all (x₀:A₀) (x₁:A₁) ... : y a₀ a1 a₂ ...

    where ``Ai`` is either a syntactical kind or a syntactical type.


Therefore each type in the context Γ can be reduced either to a syntactical kind
or a syntactical type.
