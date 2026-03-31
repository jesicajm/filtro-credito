<template>
  <div class="app-root">

    <!-- ══════════════════════════════
         VISTA 1 — FILTRO + HERO
    ══════════════════════════════ -->
    <div v-if="vista === 'filtro'" class="page-filtro">

      <header class="hero">
        <div class="hero-inner">
          <span class="eyebrow">Optimización Vehicular</span>
          <h1 class="hero-heading">
            Reduce tu cuota vehicular<br />
            <em>hasta un&nbsp;30&nbsp;%</em>
          </h1>
          <p class="hero-sub">
            Compra de cartera con optimización de seguro.
            Miles de pesos ahorrados cada mes.
          </p>
        </div>
        <div class="hero-divider"></div>
      </header>

      <section class="qs-section">
        <div class="qs-inner">

          <div class="qs-head">
            <svg viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="1.3" width="26" height="26" style="flex-shrink:0;margin-top:3px;">
              <path d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"/>
            </svg>
            <div>
              <h2 class="qs-title">Verificación de perfil</h2>
              <p class="qs-sub">Confirma los siguientes criterios para continuar</p>
            </div>
          </div>

          <!-- Card 1 — Crédito al día -->
          <div class="qcard" :class="claseCard(0, 'creditoAlDia')">
            <span class="qcard-n">01</span>
            <div class="qcard-body">
              <svg viewBox="0 0 24 24" fill="none" stroke="#cbd5e1" stroke-width="1.3" width="20" height="20" style="flex-shrink:0">
                <rect x="2" y="5" width="20" height="14" rx="2"/>
                <path d="M2 10h20"/>
              </svg>
              <p class="qcard-text">¿Tu crédito vehicular está al día?</p>
              <div class="qcard-opts">
                <button class="qbtn" :class="btnClase('creditoAlDia', true)" @click="responder('creditoAlDia', true)">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><polyline points="20 6 9 17 4 12"/></svg>
                  Sí
                </button>
                <button class="qbtn" :class="btnClase('creditoAlDia', false)" @click="responder('creditoAlDia', false)">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
                  No
                </button>
              </div>
            </div>
            <div class="qcard-badge" v-if="filtro.creditoAlDia !== null">
              <svg v-if="filtro.creditoAlDia" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2.5" width="18" height="18"><polyline points="20 6 9 17 4 12"/></svg>
              <svg v-else viewBox="0 0 24 24" fill="none" stroke="#64748b" stroke-width="2.5" width="18" height="18"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
            </div>
          </div>

          <!-- Card 2 — Reportes negativos -->
          <div class="qcard" :class="claseCard(1, 'sinReportesNegativos')">
            <span class="qcard-n">02</span>
            <div class="qcard-body">
              <svg viewBox="0 0 24 24" fill="none" stroke="#cbd5e1" stroke-width="1.3" width="20" height="20" style="flex-shrink:0">
                <path d="M9 12l2 2 4-4"/>
                <path d="M12 22c5.523 0 10-4.477 10-10S17.523 2 12 2 2 6.477 2 12s4.477 10 10 10z"/>
              </svg>
              <p class="qcard-text">¿Tienes reportes negativos en centrales de riesgo?</p>
              <div class="qcard-opts" v-if="paso >= 1">
                <button class="qbtn" :class="btnClase('sinReportesNegativos', true)" @click="responder('sinReportesNegativos', true)">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><polyline points="20 6 9 17 4 12"/></svg>
                  Sí
                </button>
                <button class="qbtn" :class="btnClase('sinReportesNegativos', false)" @click="responder('sinReportesNegativos', false)">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
                  No
                </button>
              </div>
              <p class="qcard-lock" v-else>
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" width="13" height="13"><rect x="5" y="11" width="14" height="10" rx="2"/><path d="M8 11V7a4 4 0 018 0v4"/></svg>
                Responde la pregunta anterior
              </p>
            </div>
            <div class="qcard-badge" v-if="filtro.sinReportesNegativos !== null">
              <svg v-if="filtro.sinReportesNegativos" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2.5" width="18" height="18"><polyline points="20 6 9 17 4 12"/></svg>
              <svg v-else viewBox="0 0 24 24" fill="none" stroke="#64748b" stroke-width="2.5" width="18" height="18"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
            </div>
          </div>

          <!-- Card 3 — Ingresos -->
          <div class="qcard" :class="claseCardIngresos()">
            <span class="qcard-n">03</span>
            <div class="qcard-body">
              <svg viewBox="0 0 24 24" fill="none" stroke="#cbd5e1" stroke-width="1.3" width="20" height="20" style="flex-shrink:0">
                <path d="M12 2v20M17 5H9.5a3.5 3.5 0 000 7h5a3.5 3.5 0 010 7H6"/>
              </svg>
              <p class="qcard-text">¿Tus ingresos superan los <strong>$10.000.000</strong>?</p>
              <div class="qcard-opts" v-if="paso >= 2">
                <button class="qbtn" :class="btnClase('ingresosSuperiores', true)" @click="responder('ingresosSuperiores', true)">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><polyline points="20 6 9 17 4 12"/></svg>
                  Sí
                </button>
                <button class="qbtn" :class="btnClase('ingresosSuperiores', false)" @click="responderIngresosNo">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
                  No
                </button>
              </div>
              <p class="qcard-lock" v-else>
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" width="13" height="13"><rect x="5" y="11" width="14" height="10" rx="2"/><path d="M8 11V7a4 4 0 018 0v4"/></svg>
                Responde las preguntas anteriores
              </p>

              <!-- Sub-input: monto de ingresos cuando dice No -->
              <div v-if="mostrarInputIngresos" class="income-input-wrap">
                <label class="income-label">¿Cuánto ganas mensualmente?</label>
                <div class="income-field">
                  <span class="income-prefix">$</span>
                  <input
                    ref="inputIngresos"
                    :value="ingresosFormateados"
                    @input="onIngresosInput"
                    type="text"
                    inputmode="numeric"
                    placeholder="0"
                    class="income-input"
                  />
                </div>
                <div v-if="ingresoNumerico > 0 && ingresoNumerico < 4000000" class="income-low-wrap">
                  <p class="income-warn">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" width="13" height="13"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
                    El mínimo requerido es $4.000.000
                  </p>
                  <button class="qbtn qbtn-continue qbtn-reject" @click="rechazarPorIngresos">
                    Continuar
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="12" height="12"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
                  </button>
                </div>
                <button
                  v-if="ingresoNumerico >= 4000000"
                  class="qbtn qbtn-continue"
                  @click="confirmarIngresoMedio"
                >
                  Continuar
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="12" height="12"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
                </button>
              </div>
            </div>
            <div class="qcard-badge" v-if="filtro.ingresosSuperiores !== null">
              <svg v-if="filtro.ingresosSuperiores" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2.5" width="18" height="18"><polyline points="20 6 9 17 4 12"/></svg>
              <svg v-else viewBox="0 0 24 24" fill="none" stroke="#64748b" stroke-width="2.5" width="18" height="18"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
            </div>
          </div>

          <!-- Card 4 — Vehículo modelo -->
          <div class="qcard" :class="claseCard(3, 'vehiculoModelo')">
            <span class="qcard-n">04</span>
            <div class="qcard-body">
              <svg viewBox="0 0 24 24" fill="none" stroke="#cbd5e1" stroke-width="1.3" width="20" height="20" style="flex-shrink:0">
                <path d="M5 17H3a2 2 0 01-2-2v-4a2 2 0 012-2h1l3-4h8l3 4h1a2 2 0 012 2v4a2 2 0 01-2 2h-2"/>
                <circle cx="7.5" cy="17" r="1.5"/><circle cx="16.5" cy="17" r="1.5"/>
              </svg>
              <p class="qcard-text">¿Tu vehículo es modelo <strong>2016 o superior</strong>?</p>
              <div class="qcard-opts" v-if="paso >= 3">
                <button class="qbtn" :class="btnClase('vehiculoModelo', true)" @click="responder('vehiculoModelo', true)">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><polyline points="20 6 9 17 4 12"/></svg>
                  Sí
                </button>
                <button class="qbtn" :class="btnClase('vehiculoModelo', false)" @click="responder('vehiculoModelo', false)">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" width="12" height="12"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
                  No
                </button>
              </div>
              <p class="qcard-lock" v-else>
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" width="13" height="13"><rect x="5" y="11" width="14" height="10" rx="2"/><path d="M8 11V7a4 4 0 018 0v4"/></svg>
                Responde las preguntas anteriores
              </p>
            </div>
            <div class="qcard-badge" v-if="filtro.vehiculoModelo !== null">
              <svg v-if="filtro.vehiculoModelo" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2.5" width="18" height="18"><polyline points="20 6 9 17 4 12"/></svg>
              <svg v-else viewBox="0 0 24 24" fill="none" stroke="#64748b" stroke-width="2.5" width="18" height="18"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>
            </div>
          </div>

          <!-- Progreso -->
          <div class="progress-row">
            <div class="progress-track">
              <div class="progress-fill" :style="{ width: (respondidas / 4 * 100) + '%' }"></div>
            </div>
            <span class="progress-lbl">{{ respondidas }} / 4</span>
          </div>

          <!-- CTA -->
          <button v-if="todasRespondidas" class="btn-primary" @click="irAFormulario">
            Continuar
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="14" height="14"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
          </button>

        </div>
      </section>
    </div>

    <!-- ══════════════════════════════
         VISTA 2 — RECHAZO
    ══════════════════════════════ -->
    <div v-if="vista === 'rechazo'" class="page-rechazo">
      <div class="rechazo-card">
        <div class="rechazo-ico">
          <svg viewBox="0 0 24 24" fill="none" stroke="#cbd5e1" stroke-width="1.3" width="20" height="20">
            <path d="M17 21v-2a4 4 0 00-4-4H5a4 4 0 00-4 4v2"/>
            <circle cx="9" cy="7" r="4"/>
            <path d="M23 21v-2a4 4 0 00-3-3.87M16 3.13a4 4 0 010 7.75"/>
          </svg>
        </div>
        <h3 class="rechazo-titulo">Gracias por tu interés</h3>
        <p class="rechazo-texto">
          Por ahora trabajamos con perfiles que cumplan estas condiciones.
          Déjanos tus datos y te avisamos cuando tengamos opciones para tu perfil.
        </p>
        <div class="r-grid">
          <div class="field">
            <label>Nombre completo</label>
            <input v-model="noCalifica.nombre" type="text" placeholder="Tu nombre" />
          </div>
          <div class="field">
            <label>Celular</label>
            <input v-model="noCalifica.celular" type="tel" placeholder="300 000 0000" />
          </div>
          <div class="field field-full">
            <label>Correo electrónico</label>
            <input v-model="noCalifica.email" type="email" placeholder="tu@correo.com" />
          </div>
          <div class="field field-full">
            <label class="lbl-icon">
              <svg viewBox="0 0 24 24" fill="none" stroke="#94a3b8" stroke-width="1.4" width="13" height="13">
                <rect x="3" y="4" width="18" height="18" rx="2"/>
                <line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/>
                <line x1="3" y1="10" x2="21" y2="10"/>
              </svg>
              Fecha de renovación de la póliza
            </label>
            <input v-model="noCalifica.fechaRenovacionPoliza" type="date" :min="hoy" />
          </div>
        </div>
        <button class="btn-primary" @click="guardarNoCalifica">Notifícame</button>
        <button class="btn-ghost" @click="reiniciar">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" width="13" height="13"><line x1="19" y1="12" x2="5" y2="12"/><polyline points="12 19 5 12 12 5"/></svg>
          Volver e intentarlo de nuevo
        </button>
      </div>
    </div>

    <!-- ══════════════════════════════
         VISTA 3 — FORMULARIO
    ══════════════════════════════ -->
    <div v-if="vista === 'formulario'" class="page-form">
      <div class="form-wrap">

        <header class="form-head">
          <span class="eyebrow">Optimización Vehicular</span>
          <h2 class="form-title">Información de contacto</h2>
          <div class="head-rule"></div>
        </header>

        <form @submit.prevent>
          <div class="f-grid">

            <div class="field field-full">
              <label>Tipo de crédito</label>
              <div class="sel-wrap">
                <select v-model="tipoCredito">
                  <option value="cartera">Compra de Cartera</option>
                  <option value="compraVehiculo">Compra de vehículo</option>
                </select>
                <svg viewBox="0 0 24 24" fill="none" stroke="#64748b" stroke-width="2" width="14" height="14" style="position:absolute;right:0;top:50%;transform:translateY(-50%);pointer-events:none"><polyline points="6 9 12 15 18 9"/></svg>
              </div>
            </div>

            <div class="field">
              <label>Nombre <span class="req">*</span></label>
              <input v-model="form.nombre" type="text" />
            </div>

            <div class="field">
              <label>Primer Apellido <span class="req">*</span></label>
              <input v-model="form.primerApellido" type="text" />
            </div>

            <div class="field">
              <label>Segundo Apellido</label>
              <input v-model="form.segundoApellido" type="text" />
            </div>

            <div class="field">
              <label>Celular <span class="req">*</span></label>
              <input
                :value="form.celular"
                @input="form.celular = $event.target.value.replace(/[^\d]/g, '')"
                type="text"
                inputmode="numeric"
              />
            </div>

            <div class="field field-full">
              <label>Correo electrónico <span class="req">*</span></label>
              <input v-model="form.correoElectronico" type="email" />
            </div>

            <div class="field field-full">
              <label class="lbl-icon">
                <svg viewBox="0 0 24 24" fill="none" stroke="#94a3b8" stroke-width="1.4" width="13" height="13">
                  <rect x="3" y="4" width="18" height="18" rx="2"/>
                  <line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/>
                  <line x1="3" y1="10" x2="21" y2="10"/>
                </svg>
                Fecha de renovación de la póliza
              </label>
              <input v-model="form.fechaRenovacionPoliza" type="date" :min="hoy" />
            </div>

          </div>

          <div class="form-foot">
            <button
              type="button"
              class="btn-primary"
              :class="{ 'btn-disabled': btnDeshabilitado }"
              :disabled="btnDeshabilitado || enviando"
              @click="enviar"
            >
              <span v-if="!enviando">Contactar asesor</span>
              <span v-else style="display:inline-flex;align-items:center;gap:6px">
                <svg class="spin" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="14" height="14"><circle cx="12" cy="12" r="9" stroke-dasharray="28" stroke-dashoffset="10"/></svg>
                Enviando…
              </span>
            </button>
            <p class="form-note">* Campos requeridos</p>
          </div>
        </form>

      </div>
    </div>

  </div>
</template>

<script>
/* global fbq */
export default {
  data() {
    return {
      vista: "filtro",
      paso: 0,
      filtro: {
        creditoAlDia: null,
        sinReportesNegativos: null,
        ingresosSuperiores: null,
        vehiculoModelo: null,
      },
      mostrarInputIngresos: false,
      ingresosRaw: "",
      skipMetaEvent: false,
      qualifiedEventFired: false,
      noCalifica: { nombre: "", celular: "", email: "", fechaRenovacionPoliza: "" },
      enviando: false,
      coleccionRegistros: null,
      tipoCredito: "cartera",
      form: {
        nombre: "",
        primerApellido: "",
        segundoApellido: "",
        celular: "",
        correoElectronico: "",
        fechaRenovacionPoliza: "",
      },
    };
  },
  computed: {
    respondidas() {
      return Object.values(this.filtro).filter((v) => v !== null).length;
    },
    todasRespondidas() {
      return (
        this.filtro.creditoAlDia === true &&
        this.filtro.sinReportesNegativos === false &&
        this.filtro.ingresosSuperiores !== null && this.filtro.ingresosSuperiores !== false &&
        this.filtro.vehiculoModelo === true
      );
    },
    btnDeshabilitado() {
      return !(
        this.form.nombre &&
        this.form.primerApellido &&
        this.form.celular &&
        this.form.correoElectronico
      );
    },
    hoy() {
      return new Date().toISOString().split("T")[0];
    },
    ingresoNumerico() {
      return parseInt(this.ingresosRaw, 10) || 0;
    },
    ingresosFormateados() {
      if (!this.ingresosRaw) return "";
      return Number(this.ingresosRaw).toLocaleString("es-CO");
    },
  },
  mounted() {
    if (typeof window === "undefined") return;

    import("firebase/app").then(({ initializeApp }) => {
      import("firebase/firestore").then(({ getFirestore, collection }) => {
        const app = initializeApp({
          apiKey: "AIzaSyCX6kqJyaW8d7jmAmomWNkKFEjSTEboIDg",
          authDomain: "pdf-credito-d72e6.firebaseapp.com",
          projectId: "pdf-credito-d72e6",
          storageBucket: "pdf-credito-d72e6.appspot.com",
          messagingSenderId: "13266000813",
          appId: "1:13266000813:web:f4e878c57d4e571fad1f24",
          measurementId: "G-56F8P4D7QM",
        });
        this.coleccionRegistros = collection(getFirestore(app), "registros");
      });
    });
  },
  methods: {

    // ══════════════════════════════════════
    // PIXEL HELPERS
    // ══════════════════════════════════════
    pixelTrack(event, data) {
      if (typeof fbq !== "undefined") {
        fbq("track", event, data || {});
      }
    },
    pixelCustom(event, data) {
      if (typeof fbq !== "undefined") {
        fbq("trackCustom", event, data || {});
      }
    },

    // ══════════════════════════════════════
    // ESTILOS DE CARDS
    // ══════════════════════════════════════
    claseCard(posicion, campo) {
      const val = this.filtro[campo];
      return {
        "qcard-active": this.paso === posicion && val === null,
        "qcard-ok":     val !== null && this.esRespuestaPositiva(campo, val),
        "qcard-fail":   val !== null && !this.esRespuestaPositiva(campo, val),
        "qcard-locked": this.paso < posicion,
      };
    },
    claseCardIngresos() {
      const val = this.filtro.ingresosSuperiores;
      const enPaso = this.paso === 2;
      return {
        "qcard-active": enPaso && val === null && !this.mostrarInputIngresos,
        "qcard-ok":     val === true || val === "medio",
        "qcard-fail":   val === false,
        "qcard-locked": this.paso < 2,
        "qcard-input-open": this.mostrarInputIngresos && val === null,
      };
    },
    esRespuestaPositiva(campo, val) {
      if (campo === "sinReportesNegativos") return val === false;
      if (campo === "ingresosSuperiores") return val === true || val === "medio";
      return val === true;
    },
    btnClase(campo, valor) {
      const actual = this.filtro[campo];
      if (actual === null) return {};
      if (campo === "ingresosSuperiores" && actual === "medio") {
        return {
          "qbtn-sel": valor === false,
          "qbtn-dim": valor !== false,
        };
      }
      return {
        "qbtn-sel": actual === valor,
        "qbtn-dim": actual !== valor,
      };
    },

    // ══════════════════════════════════════
    // LÓGICA DE RESPUESTAS + EVENTOS PIXEL
    // ══════════════════════════════════════
    responder(campo, valor) {
      this.filtro[campo] = valor;

      // ── PREGUNTA 1: Crédito al día ──
      if (campo === "creditoAlDia") {
        if (valor === false) {
          // ══════ PIXEL: Disqualified ══════
          this.pixelCustom("Disqualified", {
            reason: "credito_no_al_dia",
            step: 1
          });
          setTimeout(() => { this.vista = "rechazo"; }, 500);
          return;
        }
        setTimeout(() => { this.paso = 1; }, 300);
        return;
      }

      // ── PREGUNTA 2: Reportes negativos ──
      if (campo === "sinReportesNegativos") {
        if (valor === true) {
          // Sí tiene reportes negativos → rechazar
          // ══════ PIXEL: Disqualified ══════
          this.pixelCustom("Disqualified", {
            reason: "reportes_negativos",
            step: 2
          });
          setTimeout(() => { this.vista = "rechazo"; }, 500);
          return;
        }
        // No tiene reportes → avanzar
        setTimeout(() => { this.paso = 2; }, 300);
        return;
      }

      // ── PREGUNTA 3: Ingresos ──
      if (campo === "ingresosSuperiores") {
        if (valor === true) {
          this.skipMetaEvent = false;
          setTimeout(() => { this.paso = 3; }, 300);
        }
        return;
      }

      // ── PREGUNTA 4: Vehículo modelo ──
      if (campo === "vehiculoModelo") {
        if (valor === false) {
          // ══════ PIXEL: Disqualified ══════
          this.pixelCustom("Disqualified", {
            reason: "vehiculo_antiguo",
            step: 4
          });
          setTimeout(() => { this.vista = "rechazo"; }, 500);
          return;
        }
        // Pasó las 4 preguntas → calificado
        // ══════ PIXEL: Qualified ══════
        this.dispararQualified();
        setTimeout(() => { this.vista = "formulario"; }, 500);
        return;
      }
    },

    responderIngresosNo() {
      this.mostrarInputIngresos = true;
      this.$nextTick(() => {
        if (this.$refs.inputIngresos) {
          this.$refs.inputIngresos.focus();
        }
      });
    },

    onIngresosInput(e) {
      const soloDigitos = e.target.value.replace(/[^\d]/g, "");
      this.ingresosRaw = soloDigitos;
      this.$nextTick(() => {
        e.target.value = this.ingresosFormateados;
      });
    },

    confirmarIngresoMedio() {
      if (this.ingresoNumerico < 4000000) return;
      this.filtro.ingresosSuperiores = "medio";
      this.skipMetaEvent = true;
      this.mostrarInputIngresos = false;
      setTimeout(() => { this.paso = 3; }, 300);
    },

    rechazarPorIngresos() {
      this.filtro.ingresosSuperiores = false;
      this.mostrarInputIngresos = false;
      // ══════ PIXEL: Disqualified ══════
      this.pixelCustom("Disqualified", {
        reason: "ingresos_bajos",
        step: 3,
        monto: this.ingresoNumerico
      });
      setTimeout(() => { this.vista = "rechazo"; }, 500);
    },

    // ══════════════════════════════════════
    // EVENTO QUALIFIED (con protección de duplicado)
    // ══════════════════════════════════════
    dispararQualified() {
      if (this.qualifiedEventFired) return;
      this.qualifiedEventFired = true;
      this.pixelCustom("Qualified", {
        income: this.filtro.ingresosSuperiores,
        income_amount: this.ingresoNumerico || null,
        skip_meta: this.skipMetaEvent
      });
    },

    // ══════════════════════════════════════
    // IR AL FORMULARIO (botón Continuar)
    // ══════════════════════════════════════
    irAFormulario() {
      // Dispara Qualified si aún no se ha disparado
      // (respaldo en caso de que llegue por el botón sin pasar por vehiculoModelo auto-redirect)
      this.dispararQualified();

      // ══════ PIXEL: ViewContent (entró al formulario) ══════
      this.pixelTrack("ViewContent", {
        content_name: "formulario_contacto"
      });

      this.vista = "formulario";
    },

    // ══════════════════════════════════════
    // REINICIAR
    // ══════════════════════════════════════
    reiniciar() {
      this.vista = "filtro";
      this.paso  = 0;
      this.filtro = {
        creditoAlDia: null,
        sinReportesNegativos: null,
        ingresosSuperiores: null,
        vehiculoModelo: null,
      };
      this.mostrarInputIngresos = false;
      this.ingresosRaw = "";
      this.skipMetaEvent = false;
      this.qualifiedEventFired = false;
    },

    // ══════════════════════════════════════
    // GUARDAR NO CALIFICA
    // ══════════════════════════════════════
    async guardarNoCalifica() {
      if (!this.coleccionRegistros) return;
      try {
        const { addDoc } = await import("firebase/firestore");
        await addDoc(this.coleccionRegistros, {
          ...this.noCalifica,
          status: "no_califica",
          filtro: { ...this.filtro },
          timestamp: new Date(),
        });
        alert("Perfecto. Te notificaremos cuando tengamos opciones para tu perfil.");
      } catch (e) {
        console.error(e);
      }
    },

    // ══════════════════════════════════════
    // ENVIAR FORMULARIO + LEAD EVENT
    // ══════════════════════════════════════
    async enviar() {
      if (this.enviando) return;
      this.enviando = true;
      try {
        const eventId = crypto.randomUUID();
        await this.guardarRegistro(eventId);

        // ══════ PIXEL: Lead (CONVERSIÓN PRINCIPAL) ══════
        // Solo disparar si NO es skipMetaEvent (ingresos entre 4M y 10M)
        if (!this.skipMetaEvent) {
          fbq("track", "Lead", {
            event_id: eventId,
            currency: "COP",
            content_name: "compra_cartera_vehicular",
            content_category: "credito_vehicular"
          });
        }
      } catch (e) {
        console.warn(e);
      }
      window.open("https://wa.link/hxop5c", "_blank");
    },

    // ══════════════════════════════════════
    // GUARDAR EN FIREBASE
    // ══════════════════════════════════════
    async guardarRegistro(eventId) {
      if (!this.coleccionRegistros) return;
      try {
        const { ip } = await fetch("https://api.ipify.org?format=json").then((r) => r.json());
        const fbp    = document.cookie.match(/_fbp=([^;]+)/)?.[1] || null;
        const fbclid = new URLSearchParams(window.location.search).get("fbclid");
        const fbc    = fbclid || document.cookie.match(/_fbc=([^;]+)/)?.[1] || null;
        const { addDoc } = await import("firebase/firestore");
        await addDoc(this.coleccionRegistros, {
          name:                  this.form.nombre,
          lastName:              this.form.primerApellido,
          email:                 this.form.correoElectronico,
          phone:                 `57${this.form.celular.replace(/^0+/, "")}`,
          fechaRenovacionPoliza: this.form.fechaRenovacionPoliza || null,
          ingresosMensuales:     this.ingresoNumerico || null,
          ip,
          user_agent:  navigator.userAgent,
          fbp, fbc,
          event_id:    eventId,
          tipoCredito: this.tipoCredito,
          skipMetaEvent: this.skipMetaEvent,
          filtro:      { ...this.filtro },
          status:      "pendiente",
          timestamp:   new Date(),
        });
      } catch (e) {
        console.error(e);
      }
    },
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500&display=swap');

/* ════════════════════════════════
   BASE
════════════════════════════════ */
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.app-root {
  font-family: 'DM Sans', sans-serif;
  background-color: #0f1e35;
  color: #ffffff;
  min-height: 100vh;
}

button {
  font-family: 'DM Sans', sans-serif;
  cursor: pointer;
}

input, select {
  font-family: 'DM Sans', sans-serif;
}

/* ════════════════════════════════
   HERO
════════════════════════════════ */
.page-filtro {
  background-color: #0f1e35;
}

.hero {
  padding: 4.5rem 2rem 0;
  max-width: 860px;
  margin: 0 auto;
  text-align: center;
}

.eyebrow {
  display: block;
  font-family: 'DM Sans', sans-serif;
  font-size: 0.62rem;
  font-weight: 400;
  letter-spacing: 0.28em;
  text-transform: uppercase;
  color: #64748b;
  margin-bottom: 1.75rem;
}

.hero-heading {
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: clamp(2.4rem, 5.5vw, 4.2rem);
  font-weight: 400;
  line-height: 1.1;
  color: #ffffff;
  margin-bottom: 0.5rem;
}

.hero-heading em {
  font-style: italic;
  color: #e2e8f0;
}

.hero-sub {
  font-size: 0.95rem;
  font-weight: 300;
  color: #94a3b8;
  line-height: 1.8;
  margin-bottom: 3rem;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}

.hero-divider {
  width: 100%;
  height: 1px;
  background-color: rgba(255,255,255,0.08);
}

/* ════════════════════════════════
   PREGUNTAS
════════════════════════════════ */
.qs-section {
  background-color: #0f1e35;
  padding: 3rem 2rem 5rem;
}

.qs-inner {
  max-width: 680px;
  margin: 0 auto;
}

.qs-head {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 2rem;
  padding-bottom: 1.75rem;
  border-bottom: 1px solid rgba(255,255,255,0.08);
}

.qs-title {
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: 1.5rem;
  font-weight: 400;
  color: #ffffff;
  margin-bottom: 4px;
}

.qs-sub {
  font-size: 0.8rem;
  font-weight: 300;
  color: #64748b;
}

/* Cards */
.qcard {
  display: flex;
  align-items: center;
  gap: 1rem;
  background-color: #162a45;
  border: 1px solid rgba(255,255,255,0.08);
  border-left: 2px solid transparent;
  border-radius: 4px;
  padding: 1.1rem 1.3rem;
  margin-bottom: 0.65rem;
  transition: border-color 0.22s, opacity 0.22s, box-shadow 0.22s;
}

.qcard-active,
.qcard-input-open {
  border-left-color: #ffffff;
  box-shadow: 0 2px 24px rgba(0,0,0,0.35);
}

.qcard-ok {
  border-left-color: #ffffff;
}

.qcard-fail {
  border-left-color: rgba(255,255,255,0.2);
  opacity: 0.5;
}

.qcard-locked {
  opacity: 0.22;
  pointer-events: none;
}

.qcard-n {
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  color: #64748b;
  min-width: 22px;
  align-self: flex-start;
  padding-top: 2px;
}

.qcard-body {
  flex: 1;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.85rem;
}

.qcard-text {
  font-size: 0.9rem;
  font-weight: 300;
  color: #e2e8f0;
  flex: 1;
  min-width: 140px;
}

.qcard-text strong {
  font-weight: 500;
  color: #ffffff;
}

.qcard-opts {
  display: flex;
  gap: 0.45rem;
}

.qbtn {
  display: inline-flex;
  align-items: center;
  gap: 5px;
  padding: 5px 16px;
  border: 1px solid rgba(255,255,255,0.15);
  border-radius: 4px;
  background: transparent;
  font-size: 0.78rem;
  font-weight: 400;
  letter-spacing: 0.04em;
  color: #94a3b8;
  transition: all 0.16s ease;
}

.qbtn:hover {
  border-color: #ffffff;
  color: #ffffff;
}

.qbtn-sel {
  background-color: #ffffff;
  border-color: #ffffff;
  color: #0f1e35;
  font-weight: 500;
}

.qbtn-dim {
  opacity: 0.22;
}

.qbtn-continue {
  margin-top: 0.25rem;
  padding: 6px 20px;
  background-color: #ffffff;
  border-color: #ffffff;
  color: #0f1e35;
  font-weight: 500;
  animation: fadeUp 0.25s ease both;
}

.qbtn-continue:hover {
  background-color: transparent;
  color: #ffffff;
}

.qcard-lock {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 0.76rem;
  font-weight: 300;
  font-style: italic;
  color: #475569;
}

.qcard-badge {
  flex-shrink: 0;
}

/* ════════════════════════════════
   INPUT DE INGRESOS
════════════════════════════════ */
.income-input-wrap {
  width: 100%;
  margin-top: 0.5rem;
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255,255,255,0.06);
  animation: fadeUp 0.3s ease both;
}

.income-label {
  display: block;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #64748b;
  margin-bottom: 0.6rem;
}

.income-field {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  border-bottom: 1px solid rgba(255,255,255,0.15);
  padding-bottom: 0.5rem;
  margin-bottom: 0.5rem;
}

.income-prefix {
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: 1.3rem;
  color: #64748b;
}

.income-input {
  flex: 1;
  background: transparent;
  border: none;
  outline: none;
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: 1.3rem;
  color: #ffffff;
  letter-spacing: 0.02em;
}

.income-input::placeholder {
  color: rgba(255,255,255,0.12);
}

.income-low-wrap {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  animation: fadeUp 0.2s ease both;
}

.income-warn {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 0.74rem;
  font-weight: 300;
  color: #f59e0b;
}

.qbtn-reject {
  background-color: rgba(255,255,255,0.08);
  border-color: rgba(255,255,255,0.15);
  color: #94a3b8;
}

.qbtn-reject:hover {
  background-color: rgba(255,255,255,0.15);
  border-color: rgba(255,255,255,0.3);
  color: #ffffff;
}

/* Progreso */
.progress-row {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-top: 0.5rem;
  margin-bottom: 1.75rem;
}

.progress-track {
  flex: 1;
  height: 1px;
  background-color: rgba(255,255,255,0.1);
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background-color: #ffffff;
  transition: width 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.progress-lbl {
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  color: #475569;
  white-space: nowrap;
}

/* ════════════════════════════════
   BOTONES
════════════════════════════════ */
.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 0.65rem;
  padding: 0.85rem 2.25rem;
  background-color: #ffffff;
  color: #0f1e35;
  border: 1px solid #ffffff;
  border-radius: 4px;
  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  transition: background-color 0.16s, color 0.16s;
  animation: fadeUp 0.3s ease both;
}

.btn-primary:hover {
  background-color: transparent;
  color: #ffffff;
}

.btn-disabled {
  background-color: rgba(255,255,255,0.1);
  border-color: rgba(255,255,255,0.1);
  color: #475569;
  pointer-events: none;
}

.btn-ghost {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  margin-top: 1rem;
  background: none;
  border: none;
  font-size: 0.76rem;
  font-weight: 300;
  letter-spacing: 0.04em;
  color: #475569;
  transition: color 0.16s;
}

.btn-ghost:hover {
  color: #ffffff;
}

/* ════════════════════════════════
   RECHAZO
════════════════════════════════ */
.page-rechazo {
  background-color: #0f1e35;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 3rem 1.5rem;
}

.rechazo-card {
  background-color: #162a45;
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 4px;
  padding: 3rem 2.5rem;
  max-width: 460px;
  width: 100%;
  animation: fadeUp 0.4s ease;
}

.rechazo-ico {
  width: 44px;
  height: 44px;
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
}

.rechazo-titulo {
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: 1.65rem;
  font-weight: 400;
  color: #ffffff;
  margin-bottom: 0.75rem;
}

.rechazo-texto {
  font-size: 0.87rem;
  font-weight: 300;
  color: #94a3b8;
  line-height: 1.8;
  margin-bottom: 2rem;
}

.r-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
  margin-bottom: 1.75rem;
}

/* ════════════════════════════════
   FORMULARIO
════════════════════════════════ */
.page-form {
  background-color: #0f1e35;
  min-height: 100vh;
  padding: 0 2rem 5rem;
  animation: fadeUp 0.4s ease;
}

.form-wrap {
  max-width: 680px;
  margin: 0 auto;
}

.form-head {
  padding: 4.5rem 0 3rem;
  text-align: center;
}

.form-title {
  font-family: 'DM Serif Display', Georgia, serif;
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 400;
  color: #ffffff;
  margin-top: 0.9rem;
  margin-bottom: 2rem;
}

.head-rule {
  width: 48px;
  height: 1px;
  background-color: rgba(255,255,255,0.15);
  margin: 0 auto;
}

.f-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.75rem 2.25rem;
  margin-bottom: 3rem;
}

.field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.field-full {
  grid-column: 1 / -1;
}

.field label,
.lbl-icon {
  font-size: 0.62rem;
  font-weight: 400;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: #64748b;
  display: flex;
  align-items: center;
  gap: 0.4rem;
}

.req {
  color: #94a3b8;
}

.field input,
.field select {
  width: 100%;
  background: transparent;
  border: none;
  border-bottom: 1px solid rgba(255,255,255,0.12);
  padding: 0.65rem 0;
  font-size: 0.92rem;
  font-weight: 300;
  color: #ffffff;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  transition: border-color 0.18s ease;
}

.field input:focus,
.field select:focus {
  border-bottom-color: rgba(255,255,255,0.6);
}

.field input::placeholder {
  color: rgba(255,255,255,0.12);
}

.field select option {
  background-color: #162a45;
  color: #ffffff;
}

.field input[type="date"]::-webkit-calendar-picker-indicator {
  filter: invert(1);
  opacity: 0.3;
  cursor: pointer;
}

.sel-wrap {
  position: relative;
}

.form-foot {
  display: flex;
  align-items: center;
  gap: 2rem;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(255,255,255,0.08);
}

.form-note {
  font-size: 0.7rem;
  font-weight: 300;
  color: #475569;
}

/* ════════════════════════════════
   ANIMACIONES
════════════════════════════════ */
@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes rotate {
  to { transform: rotate(360deg); }
}

.spin {
  animation: rotate 0.8s linear infinite;
}

/* ════════════════════════════════
   RESPONSIVE
════════════════════════════════ */
@media (max-width: 560px) {
  .hero,
  .qs-section,
  .page-form {
    padding-left: 1.25rem;
    padding-right: 1.25rem;
  }

  .f-grid {
    grid-template-columns: 1fr;
    gap: 1.4rem;
  }

  .r-grid {
    grid-template-columns: 1fr;
  }

  .form-foot {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.9rem;
  }

  .rechazo-card {
    padding: 2rem 1.5rem;
  }
}
</style>
