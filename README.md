Conciencia-Ambiental
1. Aplicación web funcional desarrollada con Flask.
   Pantalla Inicio
  <img width="1919" height="970" alt="image" src="https://github.com/user-attachments/assets/729e7e5b-7e8f-429a-aae3-31fb0bb89e59" />
  <img width="1919" height="210" alt="image" src="https://github.com/user-attachments/assets/e5c29016-a91d-4c88-8e33-b258000efebc" />
  
  Pantalla Sistema de Gestión Ambiental
  <img width="1919" height="906" alt="image" src="https://github.com/user-attachments/assets/85599653-0b40-4e65-a340-a61370e35e8e" />
  <img width="1919" height="312" alt="image" src="https://github.com/user-attachments/assets/7578f808-dd5d-49ea-b722-3edd3192448e" />

  Pantalla Futuro del planeta
  <img width="1918" height="1028" alt="image" src="https://github.com/user-attachments/assets/5a15503b-d41b-4d64-9a5a-de44ac531c37" />

  Pantalla las 3R
  <img width="1919" height="839" alt="image" src="https://github.com/user-attachments/assets/a939be41-5ff0-46f9-94c5-b30d1b4cbb7d" />
  <img width="1919" height="536" alt="image" src="https://github.com/user-attachments/assets/2830e8a1-f1a2-457e-bfd9-fc8a5e157d43" />

  
Código fuente organizado y documentado.
app.py
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html', breadcrumb=["Inicio"])

@app.route('/sistema-ambiental')
def sistema():
    return render_template(
        'sistema.html',
        breadcrumb=["Inicio", "Sistema de Gestión Ambiental"]
    )

@app.route('/futuro')
def futuro():
    return render_template(
        'futuro.html',
        breadcrumb=["Inicio", "Futuro del Planeta"]
    )

@app.route('/tres-r')
def tres_r():
    return render_template(
        'tres_r.html',
        breadcrumb=["Inicio", "Las 3 R"]
    )

if __name__ == '__main__':
    app.run(debug=True)

base.html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Conciencia Ambiental</title>

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

    <style>
        body {
            background: linear-gradient(180deg, #f0fdf4, #ffffff);
        }

        .navbar {
            background-color: #14532d !important;
        }

        .navbar-brand,
        .nav-link {
            color: #ecfdf5 !important;
            font-weight: 500;
        }

        .nav-link:hover {
            color: #86efac !important;
        }

        h1, h2, h3 {
            color: #14532d;
        }

        .section {
            padding: 80px 0;
        }

        .img-lg {
            max-width: 95%;
            height: auto;
        }

        .info-box {
            background-color: #ecfdf5;
            border-left: 6px solid #22c55e;
            padding: 20px;
            border-radius: 12px;
            margin-top: 20px;
        }

        footer {
            background-color: #052e16;
            font-size: 0.9rem;
        }
    </style>
</head>

<body>

<nav class="navbar navbar-expand-lg navbar-dark bg-success shadow">
    <div class="container-fluid px-4">
        <a class="navbar-brand fw-bold" href="/">🌱 Medio Ambiente</a>

        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#menu">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="menu">
            <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
                <li class="nav-item">
                    <a class="nav-link" href="/">Inicio</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="/sistema-ambiental">Sistema Ambiental</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="/futuro">Futuro</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="/tres-r">3 R</a>
                </li>
            </ul>
        </div>
    </div>
</nav>

<div class="container-fluid px-4 mt-3">
    <nav aria-label="breadcrumb">
        <ol class="breadcrumb">
            {% for item in breadcrumb %}
            <li class="breadcrumb-item">{{ item }}</li>
            {% endfor %}
        </ol>
    </nav>
</div>

<main class="container-fluid px-4 mt-4">
    {% block content %}{% endblock %}
</main>

<!-- FOOTER -->
<footer class="bg-dark text-white text-center py-3 mt-5">
    🌍 Cuidar el planeta es responsabilidad de todos
</footer>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>

sistema.html
{% extends "base.html" %}
{% block content %}

<section class="section bg-light">
    <div class="content-width">
        <div class="row align-items-center g-5">

            <div class="col-lg-5 text-center">
                <img src="{{ url_for('static', filename='images/sistema.png') }}"
                    class="img-fluid img-lg rounded shadow-lg"
                    style="max-height: 300px; width: 80%; object-fit: cover;">
            </div>
            <div class="col-lg-7">
                <h1 class="fw-bold mb-4">Sistema de Gestión Ambiental</h1>

                <p class="fs-5 text-muted">
                    Un Sistema de Gestión Ambiental (SGA) es un marco estructurado
                    que permite a las organizaciones gestionar su impacto ambiental,
                    mejorar su desempeño y cumplir con normativas legales.
                </p>

                <p class="fs-5 text-muted">
                    Generalmente se basa en la norma ISO 14001:2015 y busca
                    optimizar recursos, reducir residuos y fomentar la sostenibilidad.
                </p>
            </div>
            <div class="col-lg-6 col-md-12">
                <h1>
                    ✅ <strong>Beneficios del SGA:</strong>
                </h1>
                <p class="fs-5 text-muted">
                    <ul class="mb-0">
                    <li>Reducción del impacto ambiental</li>
                    <li>Mejor uso de recursos naturales</li>
                    <li>Cumplimiento de normas ambientales</li>
                    <li>Mejor imagen institucional</li>
                </ul>
                </p>
            </div>
            <div class="col-lg-5 text-center">
                <img src="{{ url_for('static', filename='images/Beneficios.jpeg') }}"
                    class="img-fluid img-lg rounded shadow-lg"
                    style="max-height: 300px; width: 80%; object-fit: cover;">
            </div>
        </div>
    </div>
</section>

{% endblock %}

futuro.html
    {% extends "base.html" %}
    {% block content %}

    <div class="row align-items-center g-5">

        <!-- TEXTO -->
        <div class="col-lg-6 col-md-12">
            <h1 class="fw-bold mb-4">
                El planeta que dejaremos a nuestros hijos
            </h1>

            <p class="fs-5 text-muted">
                Las decisiones que tomamos hoy impactarán directamente la calidad de vida
                de las próximas generaciones. El estado actual del planeta se encuentra
                en un punto crítico, pero aún estamos a tiempo de cambiar el rumbo.
            </p>

            <p class="fs-5 text-muted">
                Los expertos coinciden en que el futuro depende de acciones
                <strong>rápidas, responsables y sostenibles</strong> tomadas desde hoy.
            </p>
        </div>

        <!-- IMAGEN -->
        <div class="col-lg-6 col-md-12 text-center">
            <img 
                src="{{ url_for('static', filename='images/futuro.jpeg') }}" 
                class="img-fluid img-lg rounded shadow-lg"
                alt="Futuro del planeta"
                style="max-height: 300px; width: 70%; object-fit: cover;">
        </div>
        <div class="col-lg-6 col-md-12">
            <h1>🌱 <strong>¿Qué podemos hacer hoy?</strong></h1> 
            
            <p class="fs-5 text-muted">
                <ul class="mb-0">
                <li>Reducir el consumo innecesario</li>
                <li>Usar energías limpias</li>
                <li>Separar residuos</li>
                <li>Educar a futuras generaciones</li>
            </ul>
            </p>
        </div>
    </div>

    {% endblock %}

tres_r.html
{% extends "base.html" %}
{% block content %}

<section class="py-5">
    <div class="container-fluid text-center">

        <h1 class="fw-bold mb-3">Las 3 R del cuidado ambiental</h1>

        <p class="fs-5 text-muted mb-4">
            Reducir, Reutilizar y Reciclar son acciones clave para disminuir
            residuos y proteger el medio ambiente.
        </p>

        <img src="{{ url_for('static', filename='images/reciclaje.jpeg') }}"
        class="img-fluid rounded shadow mb-5"
        alt="Las 3 R del cuidado ambiental"
        style="max-height: 300px; width: 50%; object-fit: cover;">


        <div class="row g-4 justify-content-center">

            <div class="col-md-4">
                <div class="card h-100 shadow-sm">
                    <div class="card-body">
                        <h4 class="card-title text-success">Reducir</h4>
                        <p class="card-text">
                            Consumir solo lo necesario ayuda a disminuir el uso excesivo
                            de recursos naturales como agua, energía y materias primas.
                        </p>
                        <ul class="text-start">
                            <li>Evitar productos desechables</li>
                            <li>Reducir el consumo de plástico</li>
                            <li>Ahorrar agua y electricidad</li>
                        </ul>
                    </div>
                </div>
            </div>

            <div class="col-md-4">
                <div class="card h-100 shadow-sm">
                    <div class="card-body">
                        <h4 class="card-title text-success">Reutilizar</h4>
                        <p class="card-text">
                            Reutilizar consiste en dar una nueva vida a los objetos
                            antes de convertirlos en basura.
                        </p>
                        <ul class="text-start">
                            <li>Usar frascos y envases nuevamente</li>
                            <li>Donar ropa y objetos en buen estado</li>
                            <li>Reparar antes de comprar nuevo</li>
                        </ul>
                    </div>
                </div>
            </div>

            <div class="col-md-4">
                <div class="card h-100 shadow-sm">
                    <div class="card-body">
                        <h4 class="card-title text-success">Reciclar</h4>
                        <p class="card-text">
                            El reciclaje permite transformar residuos en nuevos productos,
                            reduciendo la contaminación ambiental.
                        </p>
                        <ul class="text-start">
                            <li>Separar residuos correctamente</li>
                            <li>Reciclar papel, vidrio y plástico</li>
                            <li>Reducir la acumulación de basura</li>
                        </ul>
                    </div>
                </div>
            </div>

        </div>
    </div>
</section>

{% endblock %}






