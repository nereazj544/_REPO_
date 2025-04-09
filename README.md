# _REPO_

# Links de importacia
https://learn.microsoft.com/es-es/dotnet/csharp/language-reference/xmldoc/recommended-tags

# Documentacion

    Etiquetas generales usadas para varios elementos: estas etiquetas son el conjunto mínimo de cualquier API.
        <summary>: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <remarks> **
    Etiquetas usadas en miembros: estas etiquetas se usan al documentar métodos y propiedades.
        <returns>: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <param> *: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <paramref>
        <exception> *
        <value>: el valor de este elemento se muestra en IntelliSense en Visual Studio.
    Formato de salida de documentación: estas etiquetas proporcionan instrucciones de formato para las herramientas que generan documentación.
        <para>
        <list>
        <c>
        <code>
        <example> **
    Reutilización de texto de documentación: estas etiquetas proporcionan herramientas que facilitan la reutilización de comentarios XML.
        <inheritdoc> **
        <include> *
    Generación de vínculos y referencias: estas etiquetas generan vínculos a otra documentación.
        <see> *
        <seealso> *
        cref
        href
    Etiquetas para métodos y tipos genéricos: estas etiquetas solo se usan en métodos y tipos genéricos.
        <typeparam> *: el valor de este elemento se muestra en IntelliSense en Visual Studio.
        <typeparamref>
