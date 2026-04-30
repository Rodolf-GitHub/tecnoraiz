<script setup lang="ts">
import { Lightbulb, Shield, Gauge, Handshake, Leaf, Eye } from 'lucide-vue-next'

const values = [
  {
    icon: Lightbulb,
    title: 'Innovación',
    description:
      'Buscamos constantemente nuevas soluciones que integren tecnología avanzada y prácticas sostenibles.',
  },
  {
    icon: Shield,
    title: 'Seguridad',
    description: 'Cada proyecto se ejecuta con el máximo rigor técnico y cumplimiento normativo.',
  },
  {
    icon: Gauge,
    title: 'Eficiencia',
    description: 'Optimizamos recursos y procesos para brindar resultados confiables y rentables.',
  },
  {
    icon: Handshake,
    title: 'Compromiso',
    description:
      'Acompañamos a nuestros clientes con responsabilidad y cercanía, superando expectativas.',
  },
  {
    icon: Leaf,
    title: 'Sostenibilidad',
    description:
      'Promovemos energías renovables y prácticas responsables para un futuro más limpio.',
  },
  {
    icon: Eye,
    title: 'Transparencia',
    description:
      'Construimos relaciones basadas en confianza, comunicación clara y ética profesional.',
  },
]
</script>

<template>
  <div class="w-full">
    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-blue-700 to-blue-500 text-white py-16">
      <div class="max-w-6xl mx-auto px-4">
        <h1 class="text-4xl md:text-5xl font-bold">Sobre TecnoRaíz</h1>
        <p class="text-xl mt-4 text-gray-100">Ingeniería, innovación y compromiso sostenible</p>
      </div>
    </section>

    <!-- Quienes Somos Section -->
    <section class="py-16 bg-white">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-blue-700 mb-8">Quiénes Somos</h2>
        <div class="bg-blue-50 p-8 rounded-lg border-l-4 border-yellow-400">
          <p class="text-gray-700 text-lg leading-relaxed mb-4">
            En Tecno Raíz ofrecemos soluciones integrales en ingeniería eléctrica, automatización y
            energías renovables. Nacimos con la visión de simplificar la gestión técnica de hogares,
            industrias e instituciones, integrando tecnología avanzada, seguridad y eficiencia en
            cada proyecto.
          </p>
          <p class="text-gray-700 text-lg leading-relaxed">
            Nuestro equipo está formado por profesionales altamente capacitados, comprometidos con
            brindar un servicio confiable, personalizado y orientado a superar expectativas.
            Apostamos por la innovación, la sostenibilidad y el trato directo como pilares de
            nuestra propuesta.
          </p>
        </div>
      </div>
    </section>

    <!-- Founders Section -->
    <section class="py-16 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-blue-700 mb-12 text-center">Nuestros Fundadores</h2>
        <div class="grid md:grid-cols-2 gap-8">
          <div class="bg-white rounded-lg shadow-md p-8">
            <div class="flex items-center gap-4 mb-6">
              <img
                src="/fotos_de_fundadores/Liesvy.jpg"
                alt="Ing. Liesvy Delgado"
                class="w-20 h-20 rounded-full object-cover border-4 border-yellow-400"
              />
              <div>
                <h3 class="text-2xl font-bold text-blue-700">Ing. Liesvy Delgado</h3>
                <p class="text-yellow-400 font-semibold">+598 094840059</p>
              </div>
            </div>
            <p class="text-gray-700 leading-relaxed">
              Ingeniero eléctrico con más de cinco años de trayectoria en el diseño, ejecución y
              supervisión de instalaciones eléctricas de alta complejidad. Ha liderado proyectos en
              industrias de manufactura, edificios corporativos e infraestructura pública,
              garantizando soluciones seguras, eficientes y alineadas con las normativas vigentes.
              Autorizado por UTE con categoría A, combina conocimiento técnico, visión estratégica y
              compromiso con la excelencia para impulsar el crecimiento de Tecno Raíz y consolidar
              su presencia en el sector eléctrico nacional.
            </p>
          </div>
          <div class="bg-white rounded-lg shadow-md p-8">
            <div class="flex items-center gap-4 mb-6">
              <img
                src="/fotos_de_fundadores/Richard.jpg"
                alt="Ing. Richard Cruz"
                class="w-20 h-20 rounded-full object-cover border-4 border-yellow-400"
              />
              <div>
                <h3 class="text-2xl font-bold text-blue-700">Ing. Richard Cruz</h3>
                <p class="text-yellow-400 font-semibold">+598 094774616</p>
              </div>
            </div>
            <p class="text-gray-700 leading-relaxed">
              Ingeniero eléctrico especializado en instalaciones de potencia y sistemas de control,
              con sólida experiencia en proyectos residenciales, comerciales e industriales de gran
              envergadura. Ha participado en el diseño y ejecución de soluciones que garantizan
              eficiencia, seguridad y cumplimiento normativo en cada obra. Autorizado por UTE con
              categoría B, aporta conocimiento técnico, visión práctica y compromiso con la calidad,
              consolidando junto a Tecno Raíz un enfoque moderno y confiable en el sector eléctrico
              nacional.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Values Section -->
    <section class="py-16 bg-white">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-blue-700 mb-12 text-center">Nuestros Valores</h2>
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="(value, index) in values"
            :key="index"
            class="text-center bg-gray-50 p-6 rounded-lg shadow-sm hover:shadow-md transition-shadow"
          >
            <component :is="value.icon" :size="48" class="text-yellow-400 mx-auto mb-4" />
            <h3 class="text-xl font-bold text-blue-700 mb-2">{{ value.title }}</h3>
            <p class="text-gray-700">{{ value.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Mission Section -->
    <section class="bg-blue-700 text-white py-16">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold mb-8 text-center">Nuestra Misión</h2>
        <div class="bg-blue-600 p-8 rounded-lg text-center">
          <p class="text-xl leading-relaxed">
            Brindar soluciones eléctricas de alta calidad, seguras y adaptadas a las necesidades
            actuales, integrando tecnologías limpias y eficientes para contribuir a un futuro más
            sustentable.
          </p>
        </div>
      </div>
    </section>

    <!-- Why Choose Us -->
    <section class="py-16 bg-gray-50">
      <div class="max-w-6xl mx-auto px-4">
        <h2 class="text-3xl font-bold text-blue-700 mb-12 text-center">¿Por Qué Elegirnos?</h2>
        <div class="grid md:grid-cols-2 gap-8">
          <div class="flex gap-4">
            <span class="text-yellow-400 text-3xl font-bold">✓</span>
            <div>
              <h3 class="text-xl font-bold text-blue-700 mb-2">Experiencia Comprobada</h3>
              <p class="text-gray-700">
                Más de 5 años trabajando en proyectos complejos con resultados exitosos
              </p>
            </div>
          </div>
          <div class="flex gap-4">
            <span class="text-yellow-400 text-3xl font-bold">✓</span>
            <div>
              <h3 class="text-xl font-bold text-blue-700 mb-2">Atención Personalizada</h3>
              <p class="text-gray-700">
                Nos adaptamos a cada proyecto y sus necesidades específicas
              </p>
            </div>
          </div>
          <div class="flex gap-4">
            <span class="text-yellow-400 text-3xl font-bold">✓</span>
            <div>
              <h3 class="text-xl font-bold text-blue-700 mb-2">Calidad y Seguridad</h3>
              <p class="text-gray-700">
                Máximos estándares de ejecución y protección en cada instalación
              </p>
            </div>
          </div>
          <div class="flex gap-4">
            <span class="text-yellow-400 text-3xl font-bold">✓</span>
            <div>
              <h3 class="text-xl font-bold text-blue-700 mb-2">Enfoque Sostenible</h3>
              <p class="text-gray-700">
                Soluciones con energías limpias y respetuosas con el ambiente
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped></style>
