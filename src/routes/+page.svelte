<!-- src/routes/+page.svelte -->
<script>
	import { fade } from 'svelte/transition';
	import SkillPill from '$lib/components/SkillPill.svelte';
	import LanguageLevel from '$lib/components/LanguageLevel.svelte';
	import ExperienceCard from '$lib/components/ExperienceCard.svelte';

	const skills = [
		'Python',
		'TypeScript',
		'Node',
		'AWS',
		'Azure',
		'Docker',
		'Git',
		'Kubernetes',
		'Cloud Computing',
		'ETL',
		'Data Processing',
		'SQL',
		'Apache Spark',
		'Apache Airflow',
		'CI/CD',
		'Serverless Computing',
		'Lambda',
		'Microservices',
		'Backend',
		'NoSQL',
		'Linux',
		'Bash Scripting'
	];

	const experiences = [
		{
			company: 'NG.CASH',
			role: 'Data Engineer',
			period: 'Nov 2023 - Present',
			link: 'https://linkedin.com/company/ngcash',
			highlights: [
				'Optimized AWS EMR usage reducing pipeline times by 50% and costs by 60%',
				'Designed real-time monitoring system using AWS EventBridge and Lambda',
				'Developed Spark environment in VS Code with AWS EMR integration',
				'Created Python SDK for secure S3-Spark data transfers',
				'Engineered scalable pipelines with Apache Airflow and Redshift/Snowflake'
			]
		},
		{
			company: 'PwC',
			role: 'Software Engineer',
			period: 'Mar 2022 - Nov 2023',
			link: 'https://linkedin.com/company/pwc',
			highlights: [
				'Built backend portal for Azure OpenAI provisioning and multi-cloud API integration',
				'Designed Kubernetes solutions including Validating Webhook and Helm charts',
				'Developed internal automation tools using Terraform, Bicep, and ARM templates',
				'Engineered Python APIs with FastAPI for process optimization',
				'Implemented CI/CD pipelines with Azure Pipelines',
				'Created CLI tool for compliant cloud resource deployment'
			]
		},
		{
			company: 'RIO analytics',
			role: 'Data Scientist',
			period: 'Jun 2021 - Feb 2022',
			link: 'https://linkedin.com/company/rio-analytics',
			highlights: [
				'Developed and maintained ML models for time series analysis',
				'Built data mining pipelines with pandas for customer insights',
				'Established Git workflows to enhance team collaboration'
			]
		},
		{
			company: 'Bagaggio',
			role: 'BI Analyst',
			period: 'Mar 2020 - Apr 2021',
			link: 'https://linkedin.com/company/bagaggio',
			highlights: [
				'Created company-wide performance system with Excel/VBA saving thousands',
				'Developed Power BI dashboards with complex SQL queries',
				'Automated financial reports integrating multiple data sources'
			]
		},
		{
			company: 'Bagaggio',
			role: 'Logistics Intern',
			period: 'Oct 2018 - Mar 2020',
			link: 'https://linkedin.com/company/bagaggio',
			highlights: [
				'Automated Excel workflows using advanced VBA scripting',
				'SQL subject matter expert and company-wide trainer',
				'Designed Excel assessments for hiring processes'
			]
		}
	];
</script>

<svelte:head>
	<title>Victor Oliveira - Portfolio</title>
</svelte:head>

<div class="container">
	<header in:fade>
		<h1>Victor De Simone Oliveira</h1>
		<div class="contact-bar">
			<span>Rio de Janeiro, RJ, Brazil</span>
			<span>+55 21 99999-4957</span>
			<a href="mailto:victorsmoliveira@gmail.com">victorsmoliveira@gmail.com</a>
			<a href="https://linkedin.com/in/victordsm" target="_blank">LinkedIn</a>
		</div>
	</header>

	<main class="two-column-layout">
		<div class="left-column">
			<section class="skills-section" in:fade>
				<h2>Technical Skills</h2>
				<div class="skills-grid">
					{#each skills as skill}
						<SkillPill {skill} />
					{/each}
				</div>
			</section>
		</div>

		<div class="right-column">
			<section class="languages-section" in:fade>
				<h2>Languages</h2>
				<div class="language-levels">
					<LanguageLevel language="Portuguese" level={5} />
					<LanguageLevel language="English" level={5} />
					<LanguageLevel language="Spanish" level={3} />
					<LanguageLevel language="German" level={3} />
				</div>
			</section>
		</div>
	</main>

	<section class="experience-section" in:fade>
		<h2>Professional Experience</h2>
		{#each experiences as exp}
			<ExperienceCard {...exp} />
		{/each}
	</section>
</div>

<style>
	:global(*) {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		font-family: 'Inter', sans-serif;
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 1rem;
		background-color: #f5f5f5; /* Added background color */
	}

	header {
		text-align: center;
		background-color: #009688; /* Added background color */
		padding: 2rem;
		border-radius: 8px;
		color: white; /* Changed text color to white for contrast */

		h1 {
			font-size: 2.5rem;
			margin-bottom: 1rem;
		}
	}

	.contact-bar {
		display: flex;
		justify-content: center;
		gap: 1.5rem;
		flex-wrap: wrap;

		a {
			color: rgb(40, 107, 207); /* Changed link color to white for contrast */
			text-decoration: none;
			transition: opacity 0.2s;

			&:hover {
				opacity: 0.8;
				text-decoration: underline;
			}
		}
	}

	.two-column-layout {
		display: grid;
		grid-template-columns: 2fr 1fr;
		gap: 2rem;
		margin-bottom: 1rem;
	}

	.left-column {
		grid-column: 1 / 2;
	}

	.right-column {
		grid-column: 2 / 3;
	}

	.skills-section {
		h2 {
			color: #2d2d2d;
			font-size: 1.8rem;
		}
	}

	.skills-grid {
		display: flex; /* Changed to flex to allow variable width */
		flex-wrap: wrap;
		gap: 0.2rem; /* Reduced gap to make pills closer together */
	}

	.experience-section {
		grid-column: 1 / -1;
		margin-bottom: 1rem;

		h2 {
			color: #2d2d2d;
			margin-bottom: 1.5rem;
			font-size: 1.8rem;
		}
	}

	.languages-section {
		h2 {
			color: #2d2d2d;
			font-size: 1.8rem;
		}
	}

	@media (max-width: 768px) {
		.two-column-layout {
			grid-template-columns: 1fr;
		}

		.container {
			padding: 1rem;
		}

		header h1 {
			font-size: 2rem;
		}

		.contact-bar {
			flex-direction: column;
			align-items: center;
			gap: 0.5rem;
		}

		.skills-grid {
			grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
		}
	}
</style>
