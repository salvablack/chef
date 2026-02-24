import streamlit as st
import urllib.parse

# Configuración estética profesional
st.set_page_config(page_title="Chef Academy Business", page_icon="👨‍🍳", layout="centered")

# --- CONFIGURACIÓN DE CONTACTO ---
MI_WHATSAPP = "50379945643" 

# --- BASE DE DATOS DE PRODUCTOS (Marketing Culinario) ---
# Hemos diseñado los nombres para que sean aspiracionales y denoten autoridad.
FLOW = {
    "inicio": {
        "mensaje": "¡Bienvenido a la Élite Culinaria! 🔪\n¿Cómo prefieres elevar tu carrera hoy?",
        "opciones": {
            "🎓 Máster Courses": "menu_cursos",
            "💼 Business Mentoring": "menu_asesoria",
            "🔥 Ofertas Flash": "menu_promociones"
        }
    },
    # --- SECCIÓN CURSOS (5) ---
    "menu_cursos": {
        "mensaje": "Nuestros programas de formación técnica superior:",
        "opciones": {
            "Alta Cocina Pro": "curso_1",
            "Pastelería de Vanguardia": "curso_2",
            "Cocina de Autor y Creatividad": "curso_3",
            "Especialista en Parrilla Pro": "curso_4",
            "Certificación Chef Ejecutivo": "curso_5"
        }
    },
    # --- SECCIÓN ASESORÍAS (4) ---
    "menu_asesoria": {
        "mensaje": "Consultoría estratégica para dueños de restaurantes y emprendedores:",
        "opciones": {
            "Ingeniería de Menú (Rentabilidad)": "asesoria_1",
            "Estandarización de Recetas y Costos": "asesoria_2",
            "Marketing para Restaurantes": "asesoria_3",
            "Apertura de Negocios Gastronómicos": "asesoria_4"
        }
    },
    # --- SECCIÓN PROMOCIONES (5) ---
    "menu_promociones": {
        "mensaje": "Oportunidades exclusivas por tiempo limitado:",
        "opciones": {
            "Pack Emprendedor (Curso+Asesoría)": "promo_1",
            "2x1 en Cursos de Técnica": "promo_2",
            "Beca Talento (50% Dto)": "promo_3",
            "Suscripción Anual Full Pass": "promo_4",
            "Taller Masterclass de Regalo": "promo_5"
        }
    },
    # --- DETALLES DE PRODUCTOS (Puntos finales de conversión) ---
    # CURSOS
    "curso_1": {"mensaje": "👨‍🍳 **Alta Cocina Pro**: Domina las bases francesas y técnicas modernas. (Inversión: $199)", "enlace": "https://pago.com/c1", "final": True},
    "curso_2": {"mensaje": "🥐 **Pastelería de Vanguardia**: Técnicas de texturas, mousses y glaseados. (Inversión: $150)", "enlace": "https://pago.com/c2", "final": True},
    "curso_3": {"mensaje": "💡 **Cocina de Autor**: Crea tu propio sello culinario y emplatado. (Inversión: $175)", "enlace": "https://pago.com/c3", "final": True},
    "curso_4": {"mensaje": "🔥 **Parrilla Pro**: Manejo de fuegos, cortes y maduraciones. (Inversión: $120)", "enlace": "https://pago.com/c4", "final": True},
    "curso_5": {"mensaje": "🏅 **Chef Ejecutivo**: Liderazgo de brigadas y administración. (Inversión: $299)", "enlace": "https://pago.com/c5", "final": True},
    
    # ASESORÍAS
    "asesoria_1": {"mensaje": "📊 **Ingeniería de Menú**: Analizamos tu carta para subir tus ganancias un 30%.", "enlace": "https://pago.com/a1", "final": True},
    "asesoria_2": {"mensaje": "⚖️ **Costos y Recetas**: Control de mermas y estandarización total.", "enlace": "https://pago.com/a2", "final": True},
    "asesoria_3": {"mensaje": "📱 **Marketing Gastronómico**: Atrae clientes constantes a tu local.", "enlace": "https://pago.com/a3", "final": True},
    "asesoria_4": {"mensaje": "🚀 **Apertura Express**: Te acompañamos desde el plano hasta el primer plato.", "enlace": "https://pago.com/a4", "final": True},

    # PROMOCIONES
    "promo_1": {"mensaje": "🎁 **Pack Emprendedor**: Curso de Costos + Asesoría personalizada.", "enlace": "https://pago.com/p1", "final": True},
    "promo_2": {"mensaje": "👥 **2x1 Técnicas**: Compra uno y entrena a tu segundo de cocina gratis.", "enlace": "https://pago.com/p2", "final": True},
    "promo_3": {"mensaje": "🌟 **Beca Talento**: Solo 5 cupos disponibles al 50% de descuento.", "enlace": "https://pago.com/p3", "final": True},
    "promo_4": {"mensaje": "🎫 **Anual Full Pass**: Acceso a TODOS nuestros cursos por 12 meses.", "enlace": "https://pago.com/p4", "final": True},
    "promo_5": {"mensaje": "👨‍🏫 **Masterclass Regalo**: Por la compra de cualquier curso, clase de Sushi gratis.", "enlace": "https://pago.com/p5", "final": True},
}

# --- LÓGICA DEL SISTEMA ---
if "paso_actual" not in st.session_state:
    st.session_state.paso_actual = "inicio"
    st.session_state.historial = []

st.title("👨‍🍳 Chef Academy Global")
st.subheader("High Performance Gastronomy")

# Historial
for m in st.session_state.historial:
    with st.chat_message(m["rol"]):
        st.write(m["texto"])

# Paso actual
paso = FLOW[st.session_state.paso_actual]
with st.chat_message("assistant"):
    st.write(paso["mensaje"])

if "final" in paso:
    st.info("Para formalizar tu inscripción y asegurar tu cupo, completa tus datos:")
    with st.form("contacto_pro"):
        nombre = st.text_input("Nombre y Apellido:")
        tel_cliente = st.text_input("WhatsApp (Ej: +503...)")
        interes_especifico = st.text_area("¿Tienes alguna duda específica para el Chef?")
        
        if st.form_submit_button("🚀 SOLICITAR ACCESO E INFO"):
            if nombre and tel_cliente:
                # Mensaje de WhatsApp estructurado profesionalmente
                mensaje_whatsapp = (
                    f"🟢 *NUEVA SOLICITUD DE ACADEMIA*\n\n"
                    f"*Cliente:* {nombre}\n"
                    f"*WhatsApp:* {tel_cliente}\n"
                    f"*Interés:* {paso['mensaje'].split('**')[1] if '**' in paso['mensaje'] else st.session_state.paso_actual}\n"
                    f"*Dudas:* {interes_especifico if interes_especifico else 'Ninguna'}\n\n"
                    f"--- Enviado desde el Asistente Web ---"
                )
                
                url_encoded = urllib.parse.quote(mensaje_whatsapp)
                link_wa = f"https://wa.me/{MI_WHATSAPP}?text={url_encoded}"
                
                st.success("✅ ¡Perfecto! Tu ficha de inscripción está lista.")
                st.link_button("📲 Hablar con un Asesor en WhatsApp", link_wa, type="primary", use_container_width=True)
                st.link_button("💳 Pagar Ahora (Acceso Inmediato)", paso["enlace"], use_container_width=True)
            else:
                st.warning("⚠️ Los campos de Nombre y Teléfono son obligatorios para la reserva.")
else:
    st.write("---")
    # Mostrar opciones en formato lista profesional (mejor para móvil que columnas cuando son muchas)
    for texto, destino in paso["opciones"].items():
        if st.button(texto, use_container_width=True):
            st.session_state.historial.append({"rol": "user", "texto": texto})
            st.session_state.paso_actual = destino
            st.rerun()

# Botón de reinicio discreto
if st.sidebar.button("⬅️ Volver al Inicio"):
    st.session_state.paso_actual = "inicio"
    st.session_state.historial = []
    st.rerun()
